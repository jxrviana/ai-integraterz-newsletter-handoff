# → SingleBrain: One more Bird attempt tonight - revive the credential, then finish Campaign 23

We are staying on **Bird**. Do NOT use Resend - it is reserved for The Dealmaker. But campaign 23 is currently blocked by the recurring 535, so we must revive the SMTP credential BEFORE resuming. A plain resume will just 535 again.

**Step 1 - check the Bird HTTP API key.** Send one HTTP API health check to xander@usingaitoscale.com.
- If it returns 202 (valid) -> go to Step 2.
- If it now fails auth too -> the whole key is revoked. STOP and report exactly: *"Bird key fully revoked - Xander must regenerate it in the Bird dashboard."* (Xander regenerates, then we retry.)

**Step 2 - re-sync the SMTP password.** Set ListMonk's Bird SMTP password to that current valid key - this is exactly what revived sending earlier tonight (3,910 -> 8,122). Keep username `bird`, host `us1.smtp.bird.com`, port 587, STARTTLS.

**Step 3 - verify (small).** Resume campaign 23 for a small controlled amount and read the campaign log.
- If the sent counter climbs past 8,122 with NO 535 -> auth is revived, go to Step 4.
- If a 535 still appears -> the key is not usable for SMTP even after the sync. STOP and report (Xander regenerates in Bird).

**Step 4 - finish the send.** Run the native ListMonk sender at **~5 messages/second** through the rest of the list. Safe operating rules - pause and report on ANY of these:
- any complaint,
- a recurring 535 / authentication error,
- a provider rejection,
- a sustained EOF pattern (5+ EOFs in a short window),
- Bird bounce rate reaching 3% (circuit-breaker, not a target - pause earlier if hard bounces suddenly accelerate).

Tolerate isolated EOFs (let ListMonk retry them). Poll Bird ~every 5 minutes and use Bird as the source of truth. **Do NOT touch campaign 24 (The Dealmaker).**

Report at each poll and at completion - or the moment a stop condition trips. The 535 has recurred three times tonight, so if it dies again, just report where it stopped; partial progress is fine and we continue from there.
