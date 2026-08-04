# → SingleBrain: Verify with a SMALL campaign resume (the test-send isn't logging), then finish or report

The ListMonk test-send returned {"data": true} but produced NO transport log — that path gives no verifiable result, so stop using it. Use the CAMPAIGN sender, which DOES log SMTP results (you saw the 535 errors in the campaign log earlier tonight).

1. **Resume campaign 23 for a SMALL controlled amount (~50-100 messages)** on Bird, native sender, ~5 msg/sec. Watch the campaign send log and the sent counter.
   - **If the sent counter climbs past 3,910 with NO 535 in the log** -> auth is fixed. Immediately continue the native send through the REST of the list. Throttle-aware: Bird shows the domain "Throttled" (warming) — that is EXPECTED, let Bird pace it. Circuit-breaker pauses ONLY on bounce >3%, any complaint, or a recurring 535. Report Bird's cap (per hour/day), accepted vs deferred, and the running total.
   - **If you see a 535 in the campaign log** -> the Bird key lacks SMTP-send scope. STOP and report exactly: *"Campaign log shows 535 — the Bird key lacks SMTP-send scope."*

2. This small resume is SAFE: the circuit-breaker stops instantly on a 535, so at worst a handful of messages confirm the state. Do NOT socket-test from your own host again, and do NOT rely on the non-logging test-send.

Do NOT touch campaign 24 (The Dealmaker).
