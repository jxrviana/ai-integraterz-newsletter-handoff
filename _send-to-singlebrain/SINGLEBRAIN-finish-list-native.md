# → SingleBrain: Bird key verified — finish Campaign 23 natively (with a bounce circuit-breaker)

The new Bird key is confirmed good (202 accepted, no 535) and the send is healthy — 3,910 sent, landing in inbox, last real Bird bounce rate 1.70% with 0 complaints. The recent stops were all your worker/monitoring stalling (SIGTERM / exit -15), not real send problems. Let's finish the list without the choppiness.

1. **Fresh reconciliation first.** Pull Bird's CURRENT account totals (accepted, delivered, hard + out-of-band bounces, deferred, complaints) and compute the bounce rate now that 3,910 have sent.
   - If bounce rate is **<= 2% and 0 complaints** -> proceed to step 2.
   - If **> 2% or any complaints** -> pause and report instead. Do not proceed.

2. **Run the campaign to completion natively.** Do NOT spin up another custom per-wave Python worker — those keep getting killed mid-run. Instead use ListMonk's own campaign sender: set the messenger send-rate limit to ~5-8 messages/second, resume campaign 23, and let ListMonk push the remaining balance server-side to the end of the list. This keeps sending even if a monitoring script dies.

3. **Circuit-breaker while it runs.** Poll Bird's totals every ~5 minutes. **Pause the campaign immediately and report if:** the bounce rate crosses ~3%, ANY complaints appear, or Bird throttles / returns auth errors.

4. **Do NOT touch campaign 24 (The Dealmaker).**

Report the final Bird totals (accepted, delivered, bounces, complaints, bounce rate) when the list is finished — or the moment the circuit-breaker trips.
