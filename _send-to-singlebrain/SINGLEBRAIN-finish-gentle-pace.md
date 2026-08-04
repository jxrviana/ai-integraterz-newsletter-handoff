# → SingleBrain: Resume + finish Campaign 23 — gentler pace, tolerate transient EOFs

The send is healthy: 8,098 sent, 1.216% bounce, 0 complaints. The EOF that paused us is a dropped SMTP connection — almost certainly Bird's warmup THROTTLE pushing back, because 8 msg/sec across 5 connections is faster than this warming ("Throttled") domain's cap. It is not a real send failure, and ListMonk retries dropped messages.

Two changes, then run to completion:

1. **Slow the pace to stay under Bird's throttle:** drop to ~2 concurrent connections and ~2-3 messages/second. On a throttled warming domain, steady-and-slower finishes FASTER because it stops tripping the connection drops. Let ListMonk retry any dropped message.

2. **Do NOT full-stop on a single or occasional EOF.** Treat isolated EOFs as transient — log them, let ListMonk retry, keep sending. PAUSE only on:
   - any complaint,
   - a recurring 535 / authentication error,
   - a provider rejection,
   - a SUSTAINED EOF pattern (e.g. 5+ EOFs in a short window, or an EOF rate that keeps climbing) — that means a real throttle wall: pause and report,
   - Bird bounce rate reaching 3% (circuit-breaker, not a target — pause earlier if hard bounces suddenly accelerate).

3. Keep Bird as the source of truth, poll ~every 5 minutes, and **run the campaign through to the end of the list.** Report at each poll and at completion, or the moment a real stop condition trips.

Do NOT touch campaign 24 (The Dealmaker).
