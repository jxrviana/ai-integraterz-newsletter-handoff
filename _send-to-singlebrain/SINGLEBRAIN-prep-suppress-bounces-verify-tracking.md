# → SingleBrain: PREP before the Dealmaker send — suppress yesterday's bounces + PROVE tracking works

*(Xander: paste this FIRST, before the Dealmaker send message. Two prep jobs. No campaign send involved here — this is clean-up + verification only.)*

Before we send The Dealmaker, two jobs. Do both and report back **with evidence.**

## TASK A — Suppress yesterday's bounces in ListMonk
Yesterday's Referral send (Bird) produced bounces that never synced into ListMonk (the Bird→ListMonk webhook is still blocked). So they are NOT suppressed yet, and the next campaign would email them again — which hurts a fresh SMTP's reputation on its first big send.

1. **Blocklist every bounced address from yesterday's Referral send** so no future campaign can email them. Use the Bird bounce export from that send.
2. **Get the COMPLETE bounce list if you can.** We only have **52** exported, but yesterday's bounce rate (~1.68% of ~18,565) implies closer to **~300**. If you can pull the full typed bounce list from Bird, blocklist ALL of them. If Bird access still blocks a full export, blocklist the 52 we have and tell us the full export is still pending.
3. **Confirm bounce processing is ON going forward** (hard bounce → auto-blocklist) so this stops being a manual step every send.
4. **Report:** how many addresses are now on the ListMonk blocklist.

*(You do NOT need to touch any lead CSVs — Claude is cleaning the local master + niche lists separately. Your job here is only the ListMonk blocklist.)*

## TASK B — PROVE all tracking is recording (Justin needs full stats on every campaign)
Justin wants every campaign's statistics recorded so we can tell what is working and what isn't. Yesterday tracking was off and we lost all of it. Before the next send, **don't just tell us it's on — prove it with a live test.**

1. Confirm enabled, both globally and on the campaign: **open tracking, click tracking, and `individual_tracking: true`** (per-subscriber opens/clicks, not just aggregate totals).
2. **Run a live end-to-end test:** send a test to `xander@usingaitoscale.com`, then **open that email and click a link inside it.** Go back into ListMonk and confirm the **open registered AND the click registered** for that test.
3. **Report the actual evidence** — the view count and click count moving on that test (the exact numbers or a screenshot). Not "it's configured" — the actual recorded open + click.
4. Confirm the full stat set ListMonk will record and let us export **per campaign:** sent, delivered, views (opens), unique views, clicks, unique clicks, bounces, unsubscribes.

**Report back on both before we trigger The Dealmaker.** Once these are confirmed, we send the Dealmaker prep/send message next.
