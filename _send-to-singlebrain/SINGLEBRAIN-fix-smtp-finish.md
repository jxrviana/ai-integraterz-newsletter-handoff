# → SingleBrain: FIX the Bird SMTP login, then finish Campaign 23 — one shot

Diagnosis is settled: the Bird HTTP API key works (202), but ListMonk's SMTP path returns 535. Host/username/port are all correct (us1.smtp.bird.com : 587, STARTTLS, AUTH LOGIN, username `bird`). The almost-certain cause: **ListMonk's SMTP password field still holds the OLD, revoked key.** The regeneration updated the HTTP credential but not ListMonk's stored SMTP password. Fix it directly — do NOT just re-diagnose:

**Step 1 - sync the credential.** Set ListMonk's Bird SMTP **password** to the CURRENT valid Bird key — the exact credential that just passed the HTTP 202 health check. Keep username `bird`, host `us1.smtp.bird.com`, port 587, STARTTLS, AUTH LOGIN.

**Step 2 - standalone SMTP auth test (NOT the campaign).** Send ONE test message to xander@usingaitoscale.com over the SMTP path and confirm a clean 250 / accepted response, NOT a 535.

**Step 3 - branch on the result:**
- **If the SMTP test SUCCEEDS** -> resume campaign 23 (The Referral Channel, Bird) using ListMonk's NATIVE sender at ~5 messages/second and let it work through the list.
  - **Bird lists send.usingaitoscale.com as "Throttled" — it is a new, warming domain.** That is EXPECTED. Let Bird pace the send. Do NOT treat Bird throttling, deferrals, or rate-limits as a stop condition — deferred messages retry and go out as Bird's cap allows. Steady sending within Bird's limit is how the domain warms.
  - **Circuit-breaker — only real stop conditions:** poll Bird every ~5 minutes and pause + report ONLY if the bounce rate crosses ~3%, ANY complaint appears, or a 535 / auth error recurs. Throttling and deferrals are NOT stops.
  - **Also report:** Bird's current sending cap / throttle limit for this domain (per hour and per day if shown), how many messages Bird accepted vs deferred, and the running total sent. We need the real cap to plan today's remainder + tomorrow's sends.
  - Report at each ~5-minute poll, and the final totals when the list finishes OR when Bird's cap is reached for now.
- **If the SMTP test STILL returns 535** -> the working HTTP key genuinely lacks "Send via SMTP" scope. STOP and report exactly that, one line: *"The Bird key works for HTTP but lacks SMTP-send scope — Xander needs to generate a Bird Access Key with Send-via-SMTP permission."* Do not loop or retry.

**Do NOT touch campaign 24 (The Dealmaker).**

The goal is to finish Campaign 23 in this run. Steps 1-2 are very likely all it takes — apply the working key to the SMTP password, test, and let the native sender finish the list.
