# → SingleBrain: The SMTP timeout is YOUR host, not Bird — verify through ListMonk

Stop socket-testing Bird SMTP from your own environment. The timeout to us1.smtp.bird.com:587 is a limitation of YOUR VPS — cloud providers block outbound SMTP (port 587) by default. That test is meaningless here and is NOT evidence the send path is broken.

**What actually sends is ListMonk (on Railway), not your VPS.** ListMonk reaches Bird SMTP fine — it already sent 797 messages through Bird SMTP earlier tonight, and its most recent failure was a 535 (an auth REJECTION, which means it connected). The only open question is whether the password you just synced now authenticates FROM ListMonk. Verify it the right way:

1. **Trigger a ListMonk test send** for campaign 23 to xander@usingaitoscale.com using ListMonk's own test-send (e.g. `POST /api/campaigns/23/test`). This runs ListMonk -> Bird SMTP, the real path. Read ListMonk's log for the result.
   - **If it sends with no 535** -> auth is FIXED. Go to step 2.
   - **If ListMonk logs a 535** -> the key works for HTTP but lacks SMTP-send scope. STOP and report exactly that, one line: *"The Bird key works for HTTP but lacks SMTP-send scope — Xander needs a Bird Access Key with Send-via-SMTP permission."*
   - If the ListMonk test-send API isn't usable, fall back to resuming the campaign for a SMALL amount and read ListMonk's log — the circuit-breaker already stops instantly on a 535, so this is safe and self-verifying.

2. **If the test sent cleanly, resume campaign 23 natively** at ~5 msg/sec and work through the list. Bird shows the domain "Throttled" — it is warming, so that is EXPECTED. Let Bird pace it; do NOT treat throttling or deferrals as a stop. Circuit-breaker: pause + report ONLY on bounce >3%, any complaint, or a recurring 535. Report Bird's throttle cap (per hour/day), accepted vs deferred, and the running total.

Do NOT socket-test from your own host again. Do NOT touch campaign 24 (The Dealmaker).
