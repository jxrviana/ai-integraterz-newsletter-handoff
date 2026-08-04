# → SingleBrain: RESUME Campaign 23 — run to 10k, health-check, then finish

Cleared to resume. Both blockers are resolved:
- **Placement confirmed:** the send is landing in the Primary inbox (verified recipient-side).
- **Real bounce data in hand:** Bird shows 1.71% bounces (54 / 3,171) and 0 complaints — healthy for a cold list.

We no longer need the ListMonk webhook to see bounces — you can read them from Bird directly, which is what you just did. Resume:

1. **Resume campaign 23 (The Referral Channel, Bird).** Pace ~5 msg/sec, up to ~10/sec if Bird accepts cleanly. Back off immediately if Bird throttles.
2. **Wave 3: send up to ~10,000 total, then PAUSE.**
3. **At that pause, pull Bird's current account totals** (accepted, delivered, hard + out-of-band bounces, deferred, complaints) and report the bounce rate. **Do NOT auto-start the final wave** — wait for the go after we see the 10k numbers.
4. **Auto-pause and report immediately if** the Bird bounce rate crosses ~3%, ANY complaints appear, or Bird flags throttling/rate limits. Hard stops.
5. **Do NOT touch campaign 24 (The Dealmaker).**

**In parallel — do NOT let this block the send:** create the Bird -> ListMonk bounce webhook (`POST /webhooks/bounce`) and enable bounce processing so future campaigns get automated bounce/complaint monitoring. Verify with a controlled test bounce when you can. Monitoring THIS send happens via Bird per steps 3-4.

Report at the 10k pause.
