# → SingleBrain: HARD HOLD at 3,107 — get bounce tracking live before anything else

Confirmed hold. Campaign 23 stays paused at 3,107. **No sends of any kind** until we can actually see bounces and complaints — right now we can't, and that is the blocker.

Also: Wave 2 launching after I asked for a hold cannot happen again. When a message says hold / no-send, treat it as a hard gate — apply the pause and confirm the paused state BEFORE starting any worker.

Two jobs, no sending:

**1. Turn on bounce + complaint visibility (top priority).**
Right now `bounce.enabled=false`, no Bird webhook, and the bounce mailbox is still the placeholder `pop.yoursite.com` — so ListMonk's "0 bounces" is meaningless. Fix it:
- Configure Bird to POST bounce AND complaint (spam-report) events to ListMonk's authenticated bounce webhook endpoint (preferred), OR configure a real Bird return-path mailbox in ListMonk's bounce settings (replace the `pop.yoursite.com` placeholder).
- Enable bounce processing (`bounce.enabled` + webhooks).
- **Verify it actually works:** run a controlled test bounce (send to a guaranteed-bad address or Bird's test-bounce address) and confirm ListMonk records both the bounce and the complaint path.
- Report: which method you used, confirmation that the test bounce + test complaint registered, and that the live counter is now real.

**2. Give me the current Bird account totals as of now (3,107 sent).**
The earlier Bird numbers (1,062 accepted / 7 + 14 bounced / 8 deferred) predate Wave 2. Pull the CURRENT account-wide totals: accepted, delivered, hard-bounced, out-of-band bounced, deferred, rejected, complaints. Since campaign 23 is essentially the only real sending activity, account-wide is a usable estimate of our real bounce rate — report it with that caveat.

Do NOT send Wave 3. Do NOT touch campaign 24 (The Dealmaker). Once bounce tracking is verified live and I have the current totals, we confirm placement and then release the rest.
