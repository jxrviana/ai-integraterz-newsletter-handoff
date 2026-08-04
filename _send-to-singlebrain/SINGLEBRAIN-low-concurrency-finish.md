# → SingleBrain: The 535 is CONCURRENCY, not the credential - finish on Bird at low concurrency

Here is what tonight's data actually shows, at the SAME moment / same cumulative volume:
- **2 connections / 3 msg/sec -> sent cleanly** (8,122 -> 8,268, no 535).
- **5 connections / 5 msg/sec -> immediate 535.**

The Bird HTTP key tested valid (202) the whole time. So the recurring "535 invalid/revoked key" is almost certainly **Bird rejecting excess concurrent connections** on this warming / throttled account - NOT a real credential problem. The lever is LOW CONCURRENCY, not a slower per-message rate and not batching.

Also: the campaign keeps stopping because your external guard SCRIPTS crash and you pause the whole campaign when they do. Per Xander: do NOT pause the send just because a monitor script died.

Do this:

1. **Re-sync the credential** (HTTP key is valid): set ListMonk's Bird SMTP password to the current valid Bird key. username `bird`, host `us1.smtp.bird.com`, port 587, STARTTLS.

2. **Resume campaign 23 at LOW concurrency: 1-2 concurrent connections, ~2-3 messages/second** - the exact config that just worked. If a 535 or EOF still appears at 2 connections, drop to **1 connection** and continue.

3. **Monitor simply and robustly:** use ListMonk's native sender (it sends server-side) and just poll Bird's account totals with a simple curl every ~5 minutes. **If your polling/guard script crashes, RESTART it and let the campaign keep running - do NOT pause the send for a dead monitor.** ListMonk keeps sending regardless.

4. **Pause and report ONLY on a real stop condition:**
   - a recurring 535 even at 1 connection (a genuine credential death -> Xander regenerates in the Bird dashboard),
   - any complaint,
   - a provider rejection,
   - Bird bounce rate reaching 3%.
   Tolerate isolated EOFs (ListMonk retries them).

5. Run through to the end of the list - or until Bird's daily warmup cap walls us. Report progress every ~5 minutes and at completion. **Do NOT touch campaign 24 (The Dealmaker).**
