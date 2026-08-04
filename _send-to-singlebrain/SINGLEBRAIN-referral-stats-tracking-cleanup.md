# → SingleBrain: Campaign 23 cleanup + FIX tracking (do all of this, report each)

Campaign 23 (The Referral Channel) finished at 18,565 sent, ~1.68% bounce, 0 complaints — good. But there are gaps to close before we send anything else. Do every item and report results. Do NOT send any campaign mail.

## 1. Complete, TYPED bounce export (the last one was incomplete)
Your earlier export returned only **52 addresses with no bounce reason**, while Bird's counters show **~314 bounce events** (43 hard, 170 out-of-band, 84 block, 13 soft, 2 admin, 2 undetermined). That means the earlier pull missed ~260 — likely a pagination cap or it queried a single status.
- Re-pull **ALL** Campaign-23 bounces from Bird, every category, with full pagination, until the count reconciles to Bird's bounce total (~314), not 52.
- Include a **bounce_type** and **reason** column per address (hard / soft / block / out-of-band / admin, and the SMTP reason string if Bird exposes it).
- Deliver as CSV: `email, bounce_type, reason, timestamp`.

## 2. Suppress ONLY permanent bounces (do not over-suppress a warming list)
From that export, suppress in ListMonk **only the permanent / invalid-mailbox bounces**:
- **Suppress:** all **hard** bounces, plus any **block/out-of-band** whose reason is an invalid-recipient error (e.g. `550 5.1.1 no such user`, "mailbox does not exist").
- **Do NOT suppress:** soft bounces, deferrals, full-mailbox, greylisting, or reputation-based blocks — those are temporary or reputation-driven, and on a warming domain the addresses are likely valid. Removing them loses good leads.
- Report how many you suppressed and the breakdown by type.

## 3. Honor the 73 unsubscribes
Bird reported **73 unsubscribes** for this campaign. Confirm all 73 are recorded and suppressed in ListMonk so they are excluded from every future send (legal requirement). If Bird's unsubscribe events are not syncing to ListMonk, capture them and suppress them manually. Report the count reconciled.

## 4. Identify the ~491 un-sent subscribers
19,056 were on the list; ListMonk's sent counter is 18,565 — a 491 gap of subscribers never successfully sent (casualties of the 535/EOF turbulence). Query ListMonk for the subscribers on List 8 (Campaign 23 audience) that have **no successful send record** for Campaign 23, and deliver that list as CSV. **Do NOT re-send to them yet** — just identify them so we can decide on a clean re-send.

## 5. Confirm no duplicate sends
The send was paused/resumed many times. Confirm no subscriber received Campaign 23 more than once (ListMonk's per-subscriber tracking should prevent it — verify and report).

## 6. FIX engagement tracking for ALL future sends (critical)
This send went out with open/click tracking OFF (`track_opens: false`, `track_clicks: false`), so we have zero open/click data — and open rate + CTR are our primary KPIs. Before the next send:
- Enable ListMonk **open tracking and click tracking** (`track_opens` + `track_clicks`) so opens and wrapped-link clicks are recorded.
- Confirm the tracking/link domain is set correctly so wrapped links resolve.
- **Verify with a test:** send one test to xander@usingaitoscale.com, open it, click a link, and confirm ListMonk registers 1 open + 1 click. Report the result.
- From now on, **no campaign sends with tracking disabled.**

## 7. Wire the Bird -> ListMonk bounce + complaint webhook (standing task)
ListMonk shows 0 bounces because it isn't ingesting Bird's events — that's why we're hand-pulling. Configure Bird to POST bounce AND complaint events to ListMonk's bounce webhook (or a real return-path mailbox), enable bounce processing, and verify with a controlled test bounce. Once live, bounces and complaints auto-record and auto-suppress. Report when verified.

Report every section above. No campaign sends.
