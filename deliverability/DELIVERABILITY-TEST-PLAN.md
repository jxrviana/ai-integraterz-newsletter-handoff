# Deliverability Test Plan — 3-Platform Bake-off
*Goal: find which platform actually reaches inboxes, so Justin knows where to invest. Written for a first-time operator.*

## The one-paragraph version

We are sending email through three different platforms and watching where each one lands: the inbox, the Promotions tab, the spam folder, or nowhere at all. Whoever puts the most emails in front of real people wins. Each platform has a different job. **Bird** is the burner — we blast a cold list through it and we do not care if its reputation gets torched; that is literally what it is for. **JangoMail** costs real money, so it has to prove two things at once: good deliverability AND that it actually produces leads. If it can't do both, it isn't worth the price. **AutoSend** is the long-term keeper — we will NOT send cold mail through it this week. It only gets its domain connected and its warm-up started, so it stays clean for the future. This document is the step-by-step for Monday, July 20, written so someone who has never run an email test can follow it line by line.

## Before anything sends (prerequisites checklist)

Do not send a single email until every box below is checked. If one is unchecked, stop and fix it first.

- [ ] **JangoMail DNS is live and DKIM shows "verified"** in the JangoMail dashboard (the DKIM CNAME + SPF fix must read confirmed, not "pending"). No verified DKIM = no JangoMail send. Full stop.
- [ ] **Bird sending domain is confirmed verified** inside Bird, and we have written down which domain it is.
- [ ] **Bird workspace UUID is in hand** (SingleBrain needs it before it can send).
- [ ] **Seed inbox panel is built** and every address is recorded in the table further down.
- [ ] **Email content is written and approved** by Justin (subject line + body).
- [ ] **Footer has a working unsubscribe link and a real physical mailing address** (legally required — no exceptions).
- [ ] **Lead list is loaded** into the right platform and **checked against the suppression list** (anyone who previously complained or hard-bounced is removed).
- [ ] **Justin has given an explicit "GO"** in Slack for the specific send.

## The seed inbox panel (our measuring stick)

A "seed inbox" is just an email account we control and can log into to see, with our own eyes, where an email landed. A panel of them spread across the major email providers tells us whether a message hit the inbox or got filtered — the single most important number in this whole test.

Build a panel of **6–10 inboxes we control**, spread like this:
- 2–3 **Gmail** accounts
- 2 **Outlook / Hotmail** accounts
- 1–2 **Yahoo** accounts
- 1–2 **Google Workspace or custom-domain** accounts

You can create fresh accounts or use existing team addresses — both are fine for round 1. Record them in a table:

| # | Email address | Provider | Who checks it |
|---|---|---|---|
| 1 | | Gmail | |
| 2 | | Gmail | |
| 3 | | Outlook | |
| … | | | |

For **every send**, each person opens their seed inbox and marks one of four results: **Inbox / Promotions / Spam / Missing** (missing = it never arrived). That is the whole job. Paid tools like GlockApps or Inboxally can automate this later, but doing it by hand is perfectly fine for the first round.

## Monday protocol — per platform

### JangoMail (small ramp — protect this)
The JangoMail domain (scaleverticalwithai.com) is brand-new and cold — about 6 weeks old with almost no sending history — so we treat it gently or we burn the domain we are paying for.
1. **Seed-panel-only send first** — send to just the 6–10 seed inboxes (~10 emails). Confirm DKIM is verified before you touch anything.
2. **Check placement** across the panel before doing anything else.
3. **Only IF Justin hands over a warm / known list** (people who already know us and have engaged before), send **one small batch of 100–300 engaged addresses**. Stay far under the 5,000 plan cap.
4. **Never send the cold blast list through JangoMail.** That is Bird's job, not Jango's.

### Bird (the blast)
Bird is the burner, so it carries the cold list.
1. **Include the full seed panel** inside the blast so we measure placement on the same send.
2. **Volume is Justin's call** on his cold list (list size and where it came from are still TBD — get that from Justin before sending).
3. **Set expectations honestly:** a cold list on a fresh domain will produce ugly numbers — high bounces, low opens, some spam. That is expected data, not a failure. We are measuring, not hoping.

### AutoSend (no sends)
AutoSend is the keeper. We protect it by NOT using it cold.
1. **Connect the sending domain** (once the current network block is lifted).
2. **Turn on its built-in warm-up** feature.
3. **Zero campaign sends this week.** None. It just warms quietly in the background.

## What to record (per send)

Fill one row per send. Some numbers come from the platform's own reporting (SingleBrain pulls them via API); some come from humans eyeballing the seed panel. Both are marked below.

| Field | Source |
|---|---|
| Platform | — |
| Date / time sent | — |
| Volume (how many sent) | API |
| Delivered % | API |
| Bounce % | API |
| Complaint % | API |
| Seed placement (X of N: Inbox / Promotions / Spam / Missing) | Seed panel (human) |
| Opens by 24h | API |
| Clicks | API |
| Replies | API / inbox |
| Unsubscribes | API |

Leave a cell blank if the number isn't available yet — never guess or fill in a made-up figure.

## The scorecard (what Justin sees)

One table, filled in after the sends settle (give it 24 hours). This is the whole point of the exercise — the at-a-glance comparison Justin uses to decide where the money goes.

| Platform | Inbox rate (seed) | Bounce | Complaint | Opens | Replies / leads | Cost note | Verdict |
|---|---|---|---|---|---|---|---|
| Bird | | | | | | cheap burner | |
| JangoMail | | | | | | expensive — must earn it | |
| AutoSend | | | | | | keeper — warming only | |

**Three decision rules for reading it:**
1. **AutoSend is judged only after its warm-up completes** — not this week. Its row stays N/A for now; comparing a warming domain against live sends would be unfair and misleading.
2. **JangoMail must clear BOTH bars to justify its cost** — good deliverability AND real leads/replies. A great inbox rate with zero leads means it is not worth the price. It passes on both, or it is out.
3. **Any platform that trips a circuit breaker pauses immediately** — no matter how good its other numbers look. The safety rule always beats optimism.

## Circuit breakers (stop rules)

These come straight from the governance doc (§7 and Gate 3). They are not suggestions.

- **Complaint rate above 0.3% OR bounce rate above 2%** on any platform → **pause that platform's sends right away**, tell Justin, and diagnose the cause before resuming. Re-warm the domain if needed.
- **JangoMail DKIM must read "verified" before ANY JangoMail send.** No DKIM, no send — this is the Gate 3 SPF/DKIM check and it is non-negotiable.
- **If the small JangoMail seed send lands mostly in spam**, do NOT scale up to the 100–300 batch. Fix the problem first — walk the Gate 3 list (SPF/DKIM, link health, image-to-text ratio, spam score) — then retest with the seeds only.
- When in doubt, **pause and ask.** Stopping a send costs nothing; burning a paid domain costs money and weeks of recovery.

## Who does what

| Who | Owns |
|---|---|
| **Xander** (operator) | Approvals, running the seed-inbox checks by hand, giving SingleBrain its commands in Slack, escalating anything that trips a circuit breaker |
| **SingleBrain** (AI agent) | Staging the emails, sending on command, pulling delivered / bounce / complaint / open stats via API, polling DNS to confirm DKIM + SPF are verified |
| **Claude** | Writing the content, analyzing the results, building the scorecard, and calling the next step (scale, pause, or fix) |
