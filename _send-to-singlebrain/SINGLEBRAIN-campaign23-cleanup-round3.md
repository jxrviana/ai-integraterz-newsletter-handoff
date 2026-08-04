# → SingleBrain: Campaign 23 cleanup -- round 3 (ListMonk side is done; the blockers are all Bird)

Good progress -- ListMonk bounce processing + webhooks are enabled and tracking is on. The remaining blockers are Bird-side (API scope + broken pagination). Work these. No campaign list mail; only the single xander@ tracking test below is allowed.

## 1. Unsubscribe reconciliation -- use the Bird DASHBOARD, not the broken API
Bird's suppressions API pagination is malformed, so stop fighting the API for this. You have browser access -- **export the unsubscribe / suppression list from the Bird dashboard UI** (Suppressions / Unsubscribes -> export CSV). Then:
- Diff that export against ListMonk's current unsubscribed / blocklisted addresses.
- Blocklist in ListMonk every real unsubscribed address that isn't already suppressed.
- Report how many you added and the final reconciled unsubscribe count.
- If the Bird UI genuinely cannot export the list, say so plainly.

## 2. Bounce/complaint webhook -- report the exact blocker + try the mailbox fallback
Configuring the Bird webhook failed with `403 InsufficientScope` (needs `webhooks:read`). Do both:
- **Report the EXACT Bird scopes/permissions the current key is missing** to create and read webhooks, so we can request a properly-scoped Bird key. (This is the same class of problem as the earlier SMTP-send scope.)
- **Fallback that does NOT need Bird webhook scope:** configure a real bounce return-path MAILBOX in ListMonk's bounce settings (a POP/IMAP mailbox on the sending domain) so ListMonk pulls bounces directly instead of relying on a Bird webhook. Set that up if the mailbox is available; report exactly what's needed if not.
- Also: from the Bird dashboard UI, export the hard-bounce addresses for Campaign 23 and blocklist them in ListMonk.

## 3. Open/click tracking test -- coordinated with Xander
Tracking is enabled but unverified end to end. Do this:
- Send ONE test email to **xander@usingaitoscale.com only** (not the list, not campaign 23) with a tracked link.
- **Xander will open the email and click the link** -- he is expecting it.
- Then check ListMonk and confirm it recorded at least 1 open and 1 click for that test. Report the result. If nothing registers, tell me exactly which setting is still off.

## 4. Best-effort exports (accept honestly if blocked)
- **Typed Campaign-23 bounce CSV:** try the Bird dashboard UI export (Suppressions -> bounces -> export), since the API is broken. Columns: email, bounce_type, reason, timestamp.
- **The 491 unsent recipients:** try exporting List 8's subscribers from ListMonk filtered by Campaign-23 send status (subscriber export, or a direct query), rather than the campaign summary record.
- If either is still impossible, report it plainly -- do not approximate or fabricate.

Report each section.
