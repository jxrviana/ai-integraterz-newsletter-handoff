# HANDOFF — Current State

## ★ AUG 6 (LATEST) — 4 newsletters FINALIZED + zipped, drafting in ListMonk

**Staying on ListMonk** (Justin: Sendy too complex for Xander right now — Sendy + Velocity on hold). All 4 are **built, image-complete, zipped, ready to DRAFT (not send):** the Dealmaker Issue 2, The Open Source Issue 1, The Referral Channel Issue 2, Local Affiliate Pro Issue 1. Handoff: `_send-to-singlebrain/SINGLEBRAIN-draft-4-newsletters-listmonk.md` (draft-only).

**Design directions applied faithfully** (Xander supplied HTML templates; we kept style/colors/fonts, stripped the source brand, added no invented slop): Dealmaker → clean beehiiv-style, byline **Johana Buitrago**; Open Source → PhantomBuster-style, byline **Theo Marsh**, credits **Nous Research** (hermes-agent links → `nousresearch/hermes-agent`; footer keeps `github.com/jbellsolutions` as the one exposure line) + a generated logo; Referral → its **Issue 1 design reused**, byline **Jay Bell**; LAP → locked Angliss template, byline Jordan Reyes.

**Images:** all Xander-generated to the elevated editorial standard (no literal-metaphor slop, no blank paper), wired email-weight. **Copy craft added:** greeting now **`Hi {{ FirstName }},` + fallback** (not "good morning"); **restrained emphasis** (bold key stats/thesis + one accent phrase). Rules captured in `skills/general/01-creation-and-QA.md` + `05-images.md`.

**⚠️ Send gate (none SEND yet):** LAP → `localaffiliatepro.com` Safe-Browsing-flagged (draft OK, no send until Justin clears it). Dealmaker + Referral → `whimsy-nebula-47ch.here.now` ephemeral (verify before send). Open Source → clean (GitHub). All await Justin's branded CTA domain.

**Warm-up (planned, ListMonk):** `send.usingaitoscale.com` is NOT cold (~37k sent, good auth/IP). Real gate = clean CTA links + list hygiene. Plan: ~250/newsletter/day, Open Source first (clean CTA), hold consistent, ramp ~30–50%/week, verify lists (bounce <1%) + mail-tester each send. Runbook TBD. Domain how-to: `docs/DOMAIN-WARMING-SOP.md`.

---

## ★ AUG 5 (EVENING, post-huddle) — SUPERSEDES the block below where they conflict

**➡️ Full running plan: `RUNNING-TASKS.md` (root). Domain how-to: `docs/DOMAIN-WARMING-SOP.md`.**

**Platform shift — Sendy is the new PRIMARY** (self-hosted, $69 one-time, `sendy.usingaitoscale.com`). Reason: it records **per-campaign stats (opens/clicks/bounces)** — the thing ListMonk can't do. **Transferring ListMonk → Sendy.** Sends via own SMTP (Justin configures, UI-only) + SES backup; stats read from MySQL over SSH (SELECT-only agent). **Priority order now: Sendy → SendFox → Velocity.** SendFox = **blocked on payment** (AppSumo Lifetime→Pro upgrade bug; support emailed, Xander CC'd). Velocity/edcom = **least priority, don't touch** (Justin still updating it). *(This corrects the block below, which said "use SendFox now / Velocity plug-in.")* Handoff pages: Sendy `mossy-quarry-84pj.here.now`; verification playbook `grassy-lotus-k454.here.now`.

**Deliverability is now a discipline (the `localaffiliatepro.com` lesson):**
- The LAP link got **flagged by Google Safe Browsing + Razor2** (mail-tester) because we blasted ~18.5k on a **brand-new, unwarmed domain**. Auth (SPF/DKIM) + IP reputation were fine — the burned **link** was the whole problem. **LAP is HELD** until Justin clears the flag (Search Console review) or gives a clean CTA URL. Brief: `messages/TO-JUSTIN-deliverability-localaffiliatepro-flag.md`.
- **Systemic:** the standard CTA `whimsy-nebula-47ch.here.now` (on the Dealmaker + Front Desk + every niche) is the **same ephemeral-host risk**. Real fix = one stable branded CTA (`mainstreetaffiliate.com`) for all titles — Justin.
- **New rules:** bounce **<1%**, complaints **<0.1%**; **verify every list before send**; **never send From `@usingaitoscale.com`**; **warm every new domain** (buy on Justin's **Spaceship**, ~$10–20, he does DNS auth, then automated warmup — MailReach/Mailreef); always be warming + hold consistent daily volume. New QA gate (link-reputation check) added to `skills/general/01-creation-and-QA.md`.

**Roles (Justin's words):** **Xander = content (newsletters) + ops + recruiting + client management. Justin = deliverability + technical + domains/DNS.** Keep heavy deliverability with Justin.

**LAP manual send:** built correctly in ListMonk (draft, template "The Dealmaker Raw Complete HTML", 4 images hosted + rendering) — held only on the flagged link. ListMonk-ready HTML: `ready-to-send/local-affiliate-pro/index-listmonk.html`.

---

## ★ AUG 5 (LATEST) — stats in, new platforms, LAP template

**Both flagships' REAL stats (from the ESP dashboards — ListMonk can't see bounces/opens):** The Dealmaker (Resend) ~98.9% delivered / 1.1% bounce / 0.01% complaints; The Referral Channel (Bird) ~98.3% / 1.7% bounce / 0 complaints. **Healthy sends.** ⚠️ **Opens/clicks = 0 because tracking is BROKEN** (ListMonk pixel/link misconfigured; Bird had track_opens off) — not real zero engagement. Fix + Resend→ListMonk bounce webhook pending: `_send-to-singlebrain/SINGLEBRAIN-fix-tracking-and-stats.md`. Per-campaign stat method = filter the ESP dashboard by From + subject + date (not baseline-diff).

**New sending platforms (Justin's lane):** **SendFox** (use now — he's upgrading it; ⚠️ confirm it accepts custom HTML, not just its builder) + **Velocity MTA** (self-hosted MTA; plug Bird/Resend in as SMTPs). Need from Xander: the SendFox skill + merge-tag syntax + custom-HTML support; Velocity MTA docs/access.

**4 newsletter builds queued** (`_send-to-singlebrain/BUILD-1..4-*`): Dealmaker Issue 2, Local Affiliate Pro, The Open Source, Referral Issue 2 — send AFTER SingleBrain adopts the new skills (`SINGLEBRAIN-skills-NEW-direction-replace.md`; SingleBrain's skills had reverted to the OLD direction).

**Local Affiliate Pro template — ✅ LOCKED.** Xander supplied his own design (a bold "magazine" template: dark photo hero with the headline overlaid, orange logo box top-left inset, condensed headlines, an orange bar, a dark footer). LAP is built on it as **email-safe HTML** (tables + inline CSS + Arial-Narrow condensed stack — NOT Tailwind) and a **continuous story** (lead → 3 illustrated beats, no per-section buttons → one CTA). **4 images wired** (email-weight; hero darkened left/bottom for the overlay). **CTA = `https://localaffiliatepro.com/agencies/`.** Byline Jordan Reyes; From `local-affiliate-pro@send.usingaitoscale.com`. Locked file: `ready-to-send/local-affiliate-pro/index.html` (+ `images/` + `image-prompts.md`). **Future issues = change the issue number + story + 4 fresh images only; layout stays.** At send, image `src` → hosted ESP URLs.

**★ RULE — a different physical address per newsletter** (no shared footprint). ⚠️ Each must be a **REAL** address the business controls (P.O. box / virtual mailbox) — **a fabricated address is a CAN-SPAM violation AND a deliverability red flag; never invent one** (unlike bylines, which are personas). Justin to set up per-brand mailing addresses. Until then all newsletters keep the real `37460 Beacon Brick Road, Zephyrhills, FL 33541` (LAP currently uses it).

---

## ★ AUG 5 — NEW DIRECTION from Justin's huddle (read first)

**Full capture + verified: `MEETING-TAKEAWAYS-2026-08-04.md`. The newsletter model now lives in `skills/` (updated to this).**

**The pivot:** every newsletter is its own **distinct publication** — different fonts, colors, logo, images, layout, topics; no shared "footprint" (a reader who gets two the same day must never guess one sender). Universal: **white background, wider layout**; keep the formatting craft. The **one-locked-template** approach is RETIRED. Justin's 4 **types**: editorial/informational · independent-news · storytelling · promotional (`skills/general/newsletter-types.md`).
- **The Dealmaker** → editorial/informational (Brian Kurtz; Jay Abraham preeminence). ✅ Issue 1 SENT (old direct-response, 18,953); Issue 2 pivots + redesign.
- **The Referral Channel** → editorial/independent-news; must look completely different from the Dealmaker. ✅ Issue 1 SENT (18,565); next issue redesign.
- **Local Affiliate Pro** → story/StoryBrand (local businesses take back their power). Old deals-roundup SCRAPPED; rebuild story-first.
- **The Open Source** → NEW; editorial/informational via Donald Miller storytelling; anti-big-AI superhero theme; built off Justin's GitHub (github.com/jbellsolutions).
- **Niche/industry** (Front Desk, Protocol, Green Room, People Person, Daily Sun, Agency Insider) → **PURE EDUCATION — no offer, no native card, no CTA** (trust-builders). Flagships + LAP keep a mission-framed CTA.
- **Main Street Affiliate** → story flagship (Beehiiv opt-in). ⬜ To build.

**Roles:** Xander owns content/copy/editorial/storytelling; **Justin owns deliverability + SMTP + deals**. **SendFox is now an active send channel** (+ SendGrid later). **Focus niches:** health + funding + local.

**Both flagships SENT Aug 4** to the ~19k (Dealmaker via Resend 18,953; Referral via Bird 18,565). ⚠️ **ListMonk shows 0 bounces AND 0 opens/clicks — both are BLIND SPOTS, not real zeros:** no ESP→ListMonk bounce webhook (real bounces live in the Resend/Bird dashboards), and ListMonk open/click tracking is misconfigured. Stats pull + tracking fix pending (`_send-to-singlebrain/SINGLEBRAIN-campaign-stats-and-tracking-diagnosis.md`).

**Copywriting swipe file** added: `UItimate Swipe File/` (Jay Abraham, Brian Kurtz, StoryBrand, Story Sales Machine, referral/partnership) — index at `skills/general/07-swipe-file-index.md`. The copywriter-persona ecosystem is **Justin's build**.

**Skills library updated** (`skills/`): 5 newsletter skills rewritten + general skills annotated + README/newsletter-types/04-design/07-swipe-file-index; `CLAUDE.md` updated. The 5 niche re-skins from earlier Aug 4 are moot (no universal template) — niches now need their own pure-education identities.

---

**As of: Tuesday, 4 August 2026 — EOD.** Big change: after Justin's Aug-1 huddle + screenshot, the affiliate program is run as **three newsletter brands** with a clearer split — **Main Street Affiliate = a NEW Beehiiv opt-in flagship** (future), and the two **outbound** brands are **The Referral Channel** (editorial) + **The Dealmaker** (direct — the newsletter we built as "Main Street Affiliate," **renamed + rebranded Aug 1**). Footer social links **stripped** from both outbound builds.

> **New source of truth: `newsletters/00-SOURCE-OF-TRUTH.md`** (consolidates the Aug-1 screenshot + huddle; screenshot wins on conflicts). Per-newsletter specs live in `newsletters/`. `NEWSLETTER-PRIORITIES.md` is superseded by it.
> Update this file at the end of every session. Current-state, not historical.

## ★ AUG 4 (LATEST) — repo created + niche QA + deliverability dip (NEWEST — read first)

**GitHub repo created** for cross-device context: **private** repo `ai-integraterz-newsletter` (docs/specs/templates only — lead/contact CSVs, bounce CSVs, images, zips, and secrets are gitignored and stay local). Laptop Claude Code: clone it, then read README → CLAUDE.md → HANDOFF.md → **`BLOCKERS.md`** (new running list of open problems — check it).

**The 5 niche newsletters (SingleBrain-produced content, root `*-issue-001-revised.html`):** round-2 sourcing is now REAL (round 1 was fabricated; most round-2 sources independently verified live by Claude). Status:
- **Agency Insider · The People Person · The Daily Sun** — pass content QA (sources verified; a few bot-blocked but real pubs). Ready for Claude to **re-skin into the Front Desk (Rundown) design**. During re-skin: align each native card's "Power of Eight" to the real article (People Person invented a fake 8-step list).
- **The Green Room** — SingleBrain refreshing it: its 3 news stories were 6–20 mo old → asked for current (~60-day) verified PR stories. Re-skin also fixes its native headline (span→link) + footer "expressed interest" line.
- **The Protocol** — FAILED QA twice: both FDA links are 404 (SingleBrain falsely logged them 200), and 3 of 4 cards are the same 18-mo-old FDA/TRAVERSE story → sent back to refresh (max 1 FDA card with a REAL link + 1 fresh distinct story; keep native + Epic cards).
- **Labor split:** SingleBrain = research + content (must fetch-verify every link — it mis-certifies dead links, so Claude re-verifies). Claude = re-skin each into the locked Front Desk design. Xander is dropping per-niche design inspirations next.

**The Referral Channel send FINISHED at 18,565** (of ~19,056; 491 never delivered — 535/EOF casualties, unidentifiable via ListMonk API). Bird transport: ~99% delivered, **1.68% bounce, 0 complaints.** ⚠️ **Deliverability dipped:** the tracking-test (real newsletter HTML) + Bird diagnostics landed in Gmail **SPAM** (was inbox during the main send) → reputation likely dinged by the warming-domain blast. → run a real inbox-placement test + warm gradually (see `BLOCKERS.md`).

**Infra state:** ListMonk open/click tracking **ENABLED** (past send's engagement lost forever); ListMonk bounce processing **ENABLED** (hard→blocklist). **BLOCKED on Bird account access:** the webhook (Bird key lacks `webhooks` scope), unsubscribe reconciliation (~30 gap — legal, before next send), typed bounce export, and 43-hard-bounce suppression — all need a properly-scoped Bird key or an authenticated Bird dashboard session (Justin). Not urgent until the next send. Full list in `BLOCKERS.md`.

## ★ AUG 4 (END OF DAY) — Front Desk template LOCKED + Referral send done (earlier Aug 4)

**The Front Desk (gyms) is DONE and is now the LOCKED niche template.** Rebuilt as a **1:1 clone of The Rundown AI's design** (Xander's directive, after two rejected attempts that drifted to our warm house style): **black** masthead + black section bars, crisp neutral-gray page, **bronze accent** (#9a5f1d, replacing Rundown's blue), bordered white cards, layout = category → emoji+headline → image → "Image source:" → Short Version / Details / Why It Matters → Read more, star-rating sign-off, clean footer. Folder `ready-to-send/the-front-desk/` (index.html + images/s1–s4.jpg + `the-front-desk.zip`). All 4 photos generated by Xander + wired (email-weight JPGs); **all 4 external sources re-verified LIVE** (healthandfitness.org ×2, athletechnews.com, the Medium native article) with stats matching.
- **Finalization decisions (locked):** CTA → `https://whimsy-nebula-47ch.here.now/` (**cal.com retired** — a calendar/"book a call" link is too salesy for editorial); **NO sign-up link anywhere** (that opt-in is Beehiiv/Main-Street-only, not the niches); subject line **"The market's fuller than ever. Is your front desk ready?"**; From **The Front Desk `<frontdesk@send.usingaitoscale.com>`**, Reply-To `xander@usingaitoscale.com`; byline **Mara Ellison**; **no logo** (text masthead — a bell logo was generated but its cream bg clashes with the black masthead).
- **Handed to SingleBrain:** `_send-to-singlebrain/SINGLEBRAIN-frontdesk-template-and-5-niches.md` + the zip — to (a) load as a ListMonk **DRAFT** (no send) + save as the template, and (b) build the 5 remaining niches.

**Niche production model (NEW split):** SingleBrain does **research + content** per niche (its strength); **Claude re-skins each into the locked Front Desk design** (design fidelity stays with Claude — SingleBrain proved unreliable at exact design). Building **one at a time**, PAUSING after niche #1 (Agency Insider) for review. The 5: **Agency Insider · The Protocol · The Green Room · The People Person · The Daily Sun.** Native card → the shared referral-channel Medium article for now (Claude finalizes per-niche links in the re-skin).

**The Referral Channel send — the day's big time sink.** Campaign 23 on **Bird**, pushing to the ~19k list. **~14,000 sent (of ~19k) and climbing steadily at LOW concurrency** — stalled around 8k until the concurrency root-cause was found; after the fix it ran through to ~14k and is still going. Deliverability healthy throughout: **~1.34% bounce (Bird limit 5%), 0 complaints, ~99% delivered, confirmed landing in the PRIMARY inbox.** The friction was all infrastructure/pacing, not the emails:
- **Bird shows the domain "Throttled"** (it's warming) → caps rate/volume; the send is genuinely slow.
- **Recurring "535 auth failed" kept pausing it. ROOT CAUSE (found late): CONCURRENCY, not the credential** — at the same moment, 2 connections sent cleanly while 5 connections 535'd instantly. Bird rejects excess concurrent connections on a warming account as a 535. **Fix = 1–2 connections** (the config that finally ran). HTTP key stayed valid throughout.
- **Bird API key needed re-syncing** into ListMonk's SMTP password several times (HTTP key ≠ what ListMonk's SMTP had).
- **ListMonk bounce tracking is OFF** (`bounce.enabled=false`, no Bird webhook, mailbox still `pop.yoursite.com`) → Bird's dashboard is the real bounce source. **Wire the Bird→ListMonk bounce webhook later.**
- **SingleBrain's monitor scripts kept crashing** and pausing the campaign; standing instruction now = do NOT pause the send for a dead monitor, just restart the monitor (ListMonk sends server-side regardless).
- Send-thread messages all in `_send-to-singlebrain/` (latest = `SINGLEBRAIN-low-concurrency-finish.md`).

**Also Aug-4:** updated **LinkedIn messaging in Outflo**. **Local Affiliate Pro** newsletter still to finalize. **The Dealmaker Issue 1** real send (via Resend) still pending after Referral settles. Xander explicitly kept Referral on **Bird** (not Resend) — Resend stays reserved for The Dealmaker.

**Corrects the block below:** it called the Front Desk "came back broken — needs QA + rework" and the Referral send "triggered now" — both superseded by this block.

## ★ AUG 4 — SENDING IN PROGRESS + locked changes (earlier today)
**State right now:** both outbound flagships are built, tested, and loaded in ListMonk as drafts.
- **The Referral Channel** (editorial) — ListMonk campaign **23**, SMTP **Bird**, From `The Referral Channel <referral@send.usingaitoscale.com>`, Reply-To `xander@usingaitoscale.com`. Test delivered + approved. **REAL SEND to the ~19k list = triggered now via Bird.** `ready-to-send/the-referral-channel/`.
- **The Dealmaker Issue 1** (direct letter) — ListMonk campaign **24**, SMTP **Resend**, From `The Dealmaker <dealmaker@send.usingaitoscale.com>`. Test delivered + approved. Real send = **later** (a couple hours after Referral, via Resend). `ready-to-send/the-dealmaker-issue-1/`.
- **The Dealmaker Issue 2** — ⚠️ still has "AI Integraterz" + old "Jay Bell" byline + cal.com; needs the same fixes as Issue 1 (pending).
- **Send discipline:** ONE at a time. **ListMonk's SMTP is GLOBAL, not per-campaign** — set the global SMTP before each send (Bird for Referral, then Resend for Dealmaker). Nothing sends without Xander's explicit go.

**Changes locked in (ALL newsletters):**
- **NO "AI Integraterz" anywhere** — the newsletter's OWN name is the brand. Footer "© 2026 [Newsletter]"; blurb "This is [Newsletter]. We build and run…".
- **UNIQUE writer byline per newsletter:** Referral = **Jay Bell**, Dealmaker = **Johana Buitrago**, each niche its own.
- **CTA links:** Referral → `https://localaffiliatepro.com/agencies/`; Dealmaker → `https://whimsy-nebula-47ch.here.now/` (CTA text "See how it works"). cal.com retired for these two.
- **Logo** = amber handshake (`images/logo.png`) in both Dealmaker mastheads.
- **Reply-To = `xander@usingaitoscale.com` on every campaign** (From domain is send-only).
- **SMTP per newsletter for protection:** Referral=Bird, Dealmaker=Resend.

**Niches = EDITORIAL (Justin, Aug 4)** — straight news + value, NOT promotion. **6 active** (SingleBrain building one at a time): **The Front Desk** (gyms) · **Agency Insider** (marketing) · **The Protocol** (men's-health coaching) · **The Green Room** (PR) · **The People Person** (recruiting) · **The Daily Sun** (solar). **tech-B2B dropped** (general/mixed list → flagships only). **men's-health-clinics** = none (no leads). Each editorial niche's native card → **ONE shared Medium article**. ⚠️ **The Front Desk (first niche) came back broken** (box/shape issues, missing images/logo/prompts, text errors) — needs QA + rework.

**Leads:** unified master list = **`leads/final-list/ALL-LEADS-unified.csv` = 19,068** (all niches deduped + xander@/justin@ seeds) — the one CSV for flagship sends.

**SingleBrain rules in force:** ListMonk **blank/raw template (ID 8)** kills the wrapper box · **host images via ListMonk media API** · **image PROMPTS not images** (Xander generates in Higgsfield; text-safe = NO writable object in scene) · **SingleBrain runs its OWN QA + includes image prompts + Medium HTML before sending a draft** · **NO auto-send — Xander approves the preview first.**

**⚠️ Volume risk (on record):** ~19k cold per flagship on warming SMTPs may get Bird/Resend flagged or the domain blacklisted; recommended throttle + monitor + pause if flagged. Sending the full 19k is Justin's call.

## ★ WEEKEND UPDATE (Aug 3) — new infrastructure Justin built (supersedes older lines where they conflict)
Justin spent the weekend building the **sending + verification infrastructure** (his lane). What it means for us:
- **Beehiiv is LIVE → Main Street Affiliate is now buildable** (was "future"). Opt-in page: `aware-quarry-prs5.here.now`. SingleBrain has the `beehiiv` skill. ⚠️ API key returned 401 — confirm/regenerate + get the Publication ID.
- **Own SMTP server — edcom / "Partner Power Mail"** (`esp.partnerpowermail.com`, domain `partnerpowermail.com`): a standalone ESP we own (SingleBrain skill `spaceship-smtp`). Auth green (SPF/DKIM/DMARC). **COLD IP** — warm on engaged contacts, don't blast cold lists. Use as the **gray-hat tier-2 SMTP**. *(A second, Postal-based own-SMTP repo `email-infrastructure` also exists but is NOT deployed — edcom is the live one; confirm with Justin we aren't splitting effort.)*
- **Email verification API** (`verify.partnerpowermail.com` — `/verify`, `/verify/batch`, `/progress`): verify every list BEFORE importing. ~9.5k/day. Auto-processing the 49k Agency Owners list (~5 days).
- **SendFox** purchased — another sender in the mix.
- **NEW ROUTING RULE:** DELIVERABLE (verified-live) → premium tier-1 SMTP (Bird/Resend); SENDABLE (catch-all/risky) → gray-hat tier-2 (edcom). Verify → tier-split → right sender, every list.
- **New leads:** Agency Owners list — `deliverable_contacts_first10k.csv` (~4.4k) + `sendable_contacts_first10k.csv` (~8.2k). Marketing/AI agencies (some PR/staffing mixed) — needs a category check; sendable overlaps deliverable (segment by `verify_verdict`, don't double-send).
- **Kurtz 5-day welcome series** (`kurtz-list-mindset-5day-series.md`) = the Beehiiv/Main Street welcome sequence (Day-5 CTA pending).
- ⚠️ **Credentials pasted in Slack — rotate:** proxy4smtp pw, edcom login + customer key, verify API key, Beehiiv key. Handle the values directly with SingleBrain — never commit them here.
- SingleBrain catch-up brief: `_send-to-singlebrain/SINGLEBRAIN-weekend-catchup.md`.

## ★ THE STRUCTURE (Justin's core priority)
Affiliate program = THE offer for every niche. Everyone → one master list; mail the whole list, split-test. **Three affiliate brands, each a different angle on the same subject:**
1. **Main Street Affiliate** — the **opt-in flagship / front door** on **Beehiiv** (people opt in from LinkedIn, cold sends, everywhere; Justin-content-heavy). ⬜ **NEW — to build.** *(The name now belongs to this opt-in brand.)*
2. **The Referral Channel** — **editorial**, outbound. ✅ Built.
3. **The Dealmaker** — **direct-response**, outbound (JV / power-partner / Jay-Abraham "preeminence" angle; tagline *Turning relationships into revenue.*). ✅ **Built + rebranded Aug 1** — folder `ready-to-send/the-rainmaker/` (was `main-street-affiliate/`). We named it ourselves per Justin's instruction.
**Second tier = niche newsletters**, each CTA → the affiliate program; used to split-test. Specs: `newsletters/niche-*.md`.

## 🟢 NEWSLETTERS
| Newsletter | Role | Status |
|---|---|---|
| **Main Street Affiliate** (Beehiiv) | Opt-in flagship — front door | ⬜ **NEW build needed.** Not the built direct one. Spec: `newsletters/main-street-affiliate.md`. Justin-content-heavy (his screenshots/LinkedIn/results). |
| **The Dealmaker** (outbound) | Direct-response flagship | ✅ Built + rebranded `ready-to-send/the-rainmaker/` (warm ink/amber/cream, 5 images, email-safe, verified stats, CTA `cal.com/usingaitoscale/aiintegraterz`). Masthead "THE RAINMAKER", footer socials stripped + branded to The Dealmaker. Spec: `newsletters/the-rainmaker.md`. |
| **The Referral Channel** (outbound) | Editorial flagship | ✅ Built `ready-to-send/the-referral-channel/`. Medium PUBLISHED (`medium.com/@ai_integraterz/everyone-wants-a-referral-channel-...-f7d99f4f2f10`). Footer socials **stripped Aug 1**; CTA left as-is (Xander undecided on link). Spec: `newsletters/the-referral-channel.md`. |
| The People Person | Niche — recruiting | Built + in ListMonk. Card-3 CTA → `/blueprint` (swap to affiliate). |
| The Protocol (coaching) | Niche — men's health coaching | Coaching sent. Justin **loves this niche**. |
| The Protocol (clinics) | Niche — men's health clinics | Built but **blocked — 0 verified clinic leads** (re-add the 10k file). |
| The Green Room | Niche — PR | Sent — **best performer (19.67% opens)**. ListMonk-ready; used for Bird warmup. |
| Agency Insider | Niche — marketing + AI agencies | Pre-playbook draft → **rebuild**. |
| Daily Sun / gyms / tech-b2b | Niche — solar / gyms / tech | Solar = old HTML rebuild; gyms = new; **tech-b2b niche unclear (confirm).** |

## ⚙️ WHAT ACTUALLY SENDS THIS WEEK
Main Street/Beehiiv isn't built yet → this week's sends = the **two outbound** (The Dealmaker + The Referral Channel) + niche editions. **Cadence dialed WAY down from "3 sends/day" → ~2–3 sends/week, Mon/Wed/Fri.** Working split (confirm): flagship 3x/wk · Referral 2x/wk · niche 2–3x/wk. Still ~2k/day, warming.

## 📊 KPIs (Justin dictated these)
- **Open rate → 30%** (now ~22%): (1) land in **primary inbox** (deliverability), (2) **subject line**, (3) **preview text**.
- **Link clicks / traffic → 10% CTR**: (1) high-quality, (2) relevant, (3) clear **CTA**.
- **Booked calls → ≥1 per send** (traffic→booking ~1%).
- **Volume (aspirational):** ~2.5M/mo "for us," ~10M/mo business, once the list hits 50k. *Honest: 30%/10% are warm-list numbers — expect lower on cold + warming, climb toward them.*

## 🧪 SPLIT-TEST PHILOSOPHY
Control + 2–3 variants; same list at **different times** (10am vs 2/6pm), **swap times** next day; **designed vs plain** (build a plain "Sendiva-style" variant of the direct one); **editorial (Referral) vs direct (The Dealmaker)**. Put the results on LinkedIn.

## 🟢 SENDING STACK — the "triumvirate" + always one warming
- **ListMonk** = engine (open-source, SingleBrain-API-controllable). Runs **2 SMTPs**: **Bird #1** (verified, warming) + **Resend #2** (warming).
- **SendFox** = own platform + API SMTP, cheap via AppSumo lifetime (Justin acquiring).
- **Beehiiv** = flagship **opt-in** platform (Main Street Affiliate). Future-lean, but it's the front door.
- **SES** (Justin, later), SMTP.com, rotating cheap SMTPs for volume. **Always keep a 3rd warming — SMTPs WILL get shut down; that's normal, just make a new account.**
- **Plans:** **Bird $15 Startup = 50k/mo** (approved). **Resend $20 transactional = 50k/mo** (approved — Xander to buy). Contact-priced platforms rejected (too pricey vs per-send).
- **ListMonk RANDOM-splits across enabled SMTPs** → keep Bird-only enabled during controlled warmup batches. **Bird bounces don't sync → suppress manually.** Resend key stored in ListMonk DB (survives restarts — fixed the 535 bug).
- **JangoMail** — exhausted (~4,975/5,000), resets ~Aug 2. Legacy sends had no click tracking.

## 🧾 FOOTER RULE (new — reverses today's social-links add)
**Remove** LinkedIn/YouTube/Skool from footers (splits traffic, creates a footprint on Justin's personal LinkedIn, can trip spam). **Brand the footer to the newsletter's own name** (not "AI Integraterz"), but **keep the legal entity + physical address** for CAN-SPAM. ✅ Applied to The Dealmaker + The Referral Channel Aug 1.

## 🔥 BIRD WARMUP (in progress)
**Day 1 DONE (Jul 31):** Green Room → 50 clean PR leads Bird-only. 49/50 delivered (98%), 0 dupes, 1 bounce (`mark@landonagency.com` — suppress), 51% opens. **Ramp (daily, metrics-gated):** 50→100→250→500→1k→2k→4k→6k→8k→10k over ~2.5–3 wks; advance only if bounces <2%, complaints <0.1%, opens healthy. **Lead supply is the ceiling.** Next: Day 2 (100).

## 🏗️ INFRASTRUCTURE Justin asked for (Xander's lane)
- **Railway "home-base" dashboard** for Justin — all stats + the verified leads in one place (SMTPs, sends, opens, clicks, A/B, lists). Doubles as social proof. **Major to-do.**
- **Content calendar** for the sends.
- **Todd-Brown-style ListMonk sales page** (medium-form, "referrals"-themed) — sell email-sending ~$50/mo, agent-run.

## OFFER — the affiliate program
`offers/OFFER-affiliate-program.md`. Build + run a business's affiliate program; guarantee = 10 signed partners in 90 days. **Site = `mainstreetaffiliate.com`** (Justin; ~live soon). **Booking fallback = `cal.com/usingaitoscale/aiintegraterz`.** Offers we feature/promote: Pinnacle Funding · Speaker Agent · The Affiliate Machine (ours) · ConnectMed · Arizona Meals · Prelance. **NEVER "power partner" in offer copy → "affiliate program"** (the newsletter *angle/name* is the only exception).

## LEADS — final list (`leads/final-list/`, built Aug 1) — **19,066 sendable**
pr-agencies 4,272 · solar 3,632 · recruiting-staffing 3,452 · mens-health-coaching 3,289 · tech-b2b 2,293 · marketing-agencies 1,264 · gyms 931 · **mens-health-clinics 0**. Built from 3 verified batches (SmartLead-clean + Reacher-verified + Apify-valid; raw masters excluded). Justin confirmed the same totals; he's pushing the list to **50k this weekend** (data/enrichment = his lane) and will also cold-email the 19k (Instantly) Monday. **⚠️ Clinics=0** (re-add the dropped 10k file); **⚠️ tech-b2b niche unclear** (confirm).

## ✅ DOUBLE-SEND — fixed
ListMonk TEST-endpoint quirk (535 stale-password → retry stacking). Real campaigns track per-subscriber → can't double. Fixed: Resend key in ListMonk DB + pre-send gate. Re-tested clean.

## OPEN — priorities
1. ✅ **DONE — renamed/rebranded to The Dealmaker** (`ready-to-send/the-rainmaker/`), footer socials stripped. Next: **teach SingleBrain the pipeline end-to-end via skills** (message + attachment list drafted Aug 1).
2. **Build the new Main Street Affiliate on Beehiiv** (opt-in flagship, Justin-content-heavy).
3. **Referral Channel:** ✅ footer socials stripped Aug 1. CTA left as-is (Xander deciding the link).
4. **Build the plain "Sendiva-style" variant** for the designed-vs-plain test.
5. **Buy Resend $20 + Bird $15;** stand up Resend as ListMonk SMTP #2; keep a 3rd warming.
6. **Bird warmup Day 2** (100/day); suppress bounces.
7. **Railway home-base dashboard** + **content calendar** + **ListMonk sales page**.
8. Wire niche CTAs → affiliate; rebuild Daily Sun / Agency Insider; build gyms; **restore clinic 10k**; **confirm tech-b2b niche**.
9. Study: *The Overdeliver* (Kurtz) + Amber Spears; subscribe to Justin's newsletters.

## REFERENCE
- Booking (fallback CTA): `cal.com/usingaitoscale/aiintegraterz`. Offer site (pending): `mainstreetaffiliate.com`.
- Medium: `@ai_integraterz` (affiliate + clinics + coaching) · `@hiring_65676` (recruiting). 5 tags every article; publish 1/day.
- Master strategy: `newsletters/00-SOURCE-OF-TRUTH.md` · Per-newsletter: `newsletters/*.md` · Build spec: `NEWSLETTER-PLAYBOOK.md` · Full context: `CLAUDE.md`.
- Seed EVERY send with `xander@usingaitoscale.com` + `justin@usingaitoscale.com`.

## STANDING REMINDERS
- Work only in this working directory. Nothing sends without Xander's explicit approval in that turn.
- When Justin is needed: lead with the recommendation + the exact action (suggest, don't ask).
- No fabricated facts — every stat traces to a fetched source. NEVER "power partner" in offer copy. No AI slop.
- **Directory:** `newsletters/` = per-newsletter specs + source of truth. `ready-to-send/<name>/` = self-contained builds. `1-SENT/` = emailed. `leads/` (raw + `clean/` + `final-list/` + `lead-batches/`). Plus `research/` `medium/` `offers/` `deliverability/` `docs/` `design-directions/` `_send-to-singlebrain/`.
