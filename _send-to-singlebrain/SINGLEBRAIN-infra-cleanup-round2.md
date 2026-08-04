# → SingleBrain: Finish the Campaign 23 / infrastructure cleanup (no campaign sends)

Follow-up to the last cleanup. These items are still fixable. Work through each and report. **Do NOT send campaign mail to the list.** Only the two small internal tests specified below are allowed.

## 1. Reconcile unsubscribes (legal -- before any future send)
Numbers don't match: ListMonk shows 50 unsubscribed on List 8; Bird shows ~80; we earlier saw 73. Every unsubscribe must be honored.
- Pull Bird's unsubscribe / suppression list. If the messages API pagination is still broken (the `...` cursor / HTTP 422), use Bird's dedicated suppressions endpoint or export it from the Bird dashboard UI.
- Diff it against ListMonk's current unsubscribed / blocklisted addresses.
- Suppress (blocklist) in ListMonk every real unsubscribed address that isn't already suppressed.
- Report: how many were missing and are now suppressed, plus the final reconciled unsubscribe count.

## 2. Wire the Bird -> ListMonk bounce + complaint webhook
Bounce processing is enabled in ListMonk but nothing is feeding it. Finish it:
- Configure Bird to POST bounce AND complaint (spam) events to ListMonk's bounce webhook endpoint, and enable the webhook in ListMonk's bounce settings.
- Verify with a controlled test bounce (one message to a guaranteed-invalid address) and confirm ListMonk records the bounce and blocklists it. This single invalid-address test is allowed -- it is not campaign mail.
- Also pull the 43 hard-bounce addresses from Campaign 23 (via Bird's suppressions endpoint or dashboard export) and blocklist them in ListMonk now.
- Report when the webhook is live and verified.

## 3. Verify open/click tracking works (one internal test only)
Tracking is enabled (`individual_tracking: true`) but unverified. Confirm it end to end:
- Send ONE test email to **xander@usingaitoscale.com only** (not the list, not campaign 23) containing a trackable link.
- Open it and click the link.
- Confirm ListMonk records at least 1 open and 1 click.
- Report the result. If it does not register, tell me exactly which setting is still off.

## 4. Best-effort exports (report honestly if blocked)
The Bird messages API pagination returned a broken cursor last time. Try alternate paths:
- **Typed Campaign-23 bounce CSV:** use Bird's suppressions / events export or the dashboard UI instead of the messages endpoint. Columns: email, bounce_type, reason, timestamp.
- **The 491 unsent recipients:** try ListMonk's per-subscriber campaign data (the subscriber-campaign view / export, or a direct query) rather than the campaign summary record.
- If both are still impossible, say so plainly and we move on -- do not fabricate or approximate.

Report every section. No campaign mail; only the single xander@ tracking test and the one invalid-address bounce test are permitted.
