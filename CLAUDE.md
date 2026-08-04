# CLAUDE.md — AI Integraterz Newsletter Project

Standing context for this folder. Read this first, then `HANDOFF.md` for where things stand today.

---

## STANDING RULES (hard rules, not preferences)

1. **SUGGEST, DON'T ASK.** (Justin's direct feedback, 2026-07-24.) When something is needed from Justin, lead with a recommendation and the exact action — never a bare list of questions. Format: "Here is what I suggest, here is what I need from you." This is the single most important working rule on this project.
2. **Never deploy, publish, or touch Xander's hosting accounts without explicit permission in that turn.** Prior incident: agents were spawned to deploy to his Vercel after he said "solve this problem." That was not consent. Deflection is not approval. ESPs host their own images — that is the correct path.
3. **Work only inside this working directory.** Never search or read `Downloads`, `Desktop`, `Documents`, or anywhere else on the machine — not even to locate a file the user mentioned. If something is needed, **ask Xander to place it in this folder.** The same applies to any subagent brief.
4. **Every newsletter ships as a rendered HTML file with images** that Xander can open and look at. Never markdown only.
4. **Heavy work goes to Opus 4.8 subagents** with precise, complete instructions. Claude orchestrates; agents execute.
5. **Nothing sends without explicit approval.** Drafts and test sends only.
6. **No fabricated facts, ever.** Every statistic must trace to a real fetched source. Vendor research is labelled as vendor research. If a number cannot be verified, it does not ship. The whole product rests on this discipline.

**Working style:** Xander is a beginner at email/newsletter operations. Plain English, no unexplained jargon, step-by-step direction. Claude drafts and directs; Xander executes in the UIs.

---

## THE PROJECT

Xander works for **Justin Bellware** at **AI Integraterz** (also operates as **Using AI To Scale**). Justin is the boss and wants ownership and initiative from Xander.

The work: **outbound newsletters** — cold emails formatted as genuine trade newsletters. The reader experiences a real publication. The company's own offer appears as **ONE story block styled identically to the news around it**, plus one short blurb at the bottom.

**The offer is the affiliate program** (we build + run a business's affiliate program — partners sell their offer on commission). It's the CTA for every newsletter. The program runs as **three affiliate flagship brands** — *Main Street Affiliate* (Beehiiv **opt-in** flagship, to build), *The Referral Channel* (editorial **outbound**), *The Dealmaker* (direct-response **outbound**, JV/power-partner angle) — all mailed to one master list + split-tested, plus a **niche-newsletter tier** whose CTAs also point to the affiliate program. **Full current model + per-newsletter specs live in `newsletters/` — start with `newsletters/00-SOURCE-OF-TRUTH.md`.**

Justin's directive, on the MyClaw newsletter he sent as reference: their own product announcement sits at story position 3 "but it looks like another article... they just plugged it in there to get more clicks through to their site. We want to do the exact same."

---

## PEOPLE AND AGENTS

- **Justin Bellware** — boss. justin@usingaitoscale.com.
- **SingleBrain** — AI agent in Slack. Owns the ESP/sending side (ListMonk + Bird/Resend; JangoMail legacy): builds campaigns, uploads images, sends tests + real sends. **Being taught the full pipeline end-to-end via skills** (research → copy → images → HTML → Medium → QA → test → send). AgentMail inbox `singlebrainslack@agentmail.to`. Runs on a VPS at 137.184.151.136.
- **The Operator** — separate Notion/project-management agent Justin runs. Tracks tasks in a Notion project called `📰 Newsletters`.
- **Claude (this session)** — owns content: research, writing, images, HTML, quality control.

---

## THE NEWSLETTERS

> **★ NEW DIRECTION (Aug 4–5 huddle — supersedes the older format/offer rules further down this file). Full capture: `MEETING-TAKEAWAYS-2026-08-04.md`. Per-newsletter detail: `skills/newsletters/`.**

**Every newsletter is its own DISTINCT PUBLICATION** — its own persona, mission, and look (fonts, colors, logo, images, layout, topics). No shared "footprint": someone who receives two in a day must never guess they're from the same sender. **Keep the formatting craft** (good-morning intro, bolds, text blocks, Short Version/Details/Why It Matters, quote blocks) — change the LOOK + identity per newsletter. Universal: **white background, wider layout.** The old "one locked Front Desk template for all niches" is **RETIRED.**

**Newsletter types (Justin's taxonomy):** editorial/informational (MyClaw) · editorial/independent-news (Substack — Zeteo, Breaking Points) · storytelling (Bill Mueller / Story Sales Machine) · promotional (Sendivo).

**The newsletters + type/mission:**
- **The Dealmaker** — *editorial/informational, Brian Kurtz style.* Jay Abraham + "preeminence." ✅ Issue 1 sent (old direct-response version); Issue 2 pivots. `skills/newsletters/the-dealmaker.md`
- **The Referral Channel** — *editorial/independent news.* Must look completely different from the Dealmaker. ✅ Issue 1 sent; next issue redesigned. `skills/newsletters/the-referral-channel.md`
- **Local Affiliate Pro** — *story/StoryBrand.* Mission: local "Main Street" businesses take back their power (networking→affiliate); breaking free of Big-Tech ads. (Scrap the old deals-roundup.) `skills/newsletters/local-affiliate-pro.md`
- **The Open Source** — *editorial/informational via Donald Miller storytelling. NEW — to build.* Superhero / anti-big-AI; a small group giving AI away free; built off Justin's GitHub (github.com/jbellsolutions). `skills/newsletters/the-open-source.md`
- **Main Street Affiliate** — *story / Story Sales Machine.* The Beehiiv **opt-in** flagship. ⬜ To build.
- **Niche / industry newsletters** — The Front Desk (gyms), The Protocol (men's-health coaching), The Green Room (PR), The People Person (recruiting), The Daily Sun (solar), Agency Insider (marketing/AI). *Editorial/informational.* ⚠️ **PURE EDUCATION — NO advert, NO bottom CTA, NO native affiliate card.** Job = build trust only; conversion happens elsewhere. Each gets its own look.

**Focus niches going forward:** HEALTH (coaches/clinics) + FUNDING (7-figure) + LOCAL affiliates (solar / home services). PR + others kept only for engagement.

**Roles:** **Xander owns content/copy/editorial/storytelling/mission; Justin owns deliverability + SMTP + deals.**

---

## THE STACK (current — live detail in `HANDOFF.md`)

- **ListMonk = the sending engine** (open-source, SingleBrain-API-controllable, on Railway). Runs **two SMTPs**: **Bird #1** (verified, warming; $15 Startup = 50k/mo) + **Resend #2** ($20 transactional = 50k/mo). Sending domain `send.usingaitoscale.com`. **Always keep a 3rd SMTP warming** — SMTPs get shut down; that's normal, just make a new account.
- **SendFox** — own newsletter platform + API SMTP (AppSumo lifetime; Justin acquiring).
- **Beehiiv** — the **opt-in** flagship platform (Main Street Affiliate). Future — not set up yet.
- **JangoMail** — legacy/side-test ESP (~5k cap, resets monthly). Domain `scaleverticalwithai.com`. Old sends had no click tracking.
- **SmartLead** — lead-list source (Xander pulls). Verified leads consolidated in `leads/final-list/`.
- **Higgsfield** — image generation (GPT Image 2 = model of record; `gpt_image_2` defaults to LOW quality — always force `quality:"high"`; `nano_banana_pro` silently aliases to `nano_banana_2`).
- **DNS at Hostinger** — Xander has NO access; Justin does.

---

## KEY FACTS AND LINKS

- Footer brand = **the newsletter's own name** (e.g. "The Dealmaker"), not "AI Integraterz". **NEVER print "Published by AI Integraterz" — or "AI Integraterz" in any form — anywhere in a newsletter** (all AII branding stripped; Xander, 2026-08-04). Keep **only the physical address** for CAN-SPAM compliance (the address alone satisfies the law). **No social links in the footer** (playbook rule 25).
- Legal entity: **AI Integraterz** · Physical address: **37460 Beacon Brick Road, Zephyrhills, Florida 33541**
- Case studies (both verified live; web pages despite the `.pdf` extension):
  `https://aiintegraterz.com/case-studies/mens-health.pdf` · `https://aiintegraterz.com/case-studies/recruiting.pdf`
- SpeakerAgent AI: `https://speakeragent.ai/`
- Medium articles used as the "source" for story 3:
  Men's health — `https://medium.com/@ai_integraterz/mens-health-clinics-can-t-really-advertise-here-s-what-they-build-instead-fd08ff27f8df`
  Recruiting — `https://medium.com/@hiring_65676/how-recruiting-firms-are-getting-in-the-room-before-the-req-opens-0205c53cb00e`

---

## THE BUILD PIPELINE (proven, reusable)

Research (Opus agent, verified sources) → markdown draft against the playbook → images (Opus agent, Higgsfield, photorealistic, a different model per slot) → email HTML build (Opus agent) → Claude QA (stat tracing, link check, format-parity check, render check) → zip → SingleBrain loads into the ESP (ListMonk + Bird/Resend) → test send → approval → send. **This pipeline is being packaged as skills so SingleBrain can run it end-to-end at scale — Claude architects + QA's; a human/Claude review gate always precedes a real send.**

---

## THE FORMAT (summary — full spec in `NEWSLETTER-PLAYBOOK.md`)

> ⚠️ **Superseded (Aug 4–5): the below is the OLD universal editorial news-card format — it no longer applies to every newsletter.** Format now varies by TYPE (story/StoryBrand for Local Affiliate Pro & Main Street; independent-news for The Referral Channel; Donald-Miller storytelling for The Open Source). **Niche/industry newsletters are now pure education: NO card-3 native ad, NO mention budget, no bottom CTA.** Per-newsletter format lives in `skills/newsletters/`. The formatting *craft* described below (card structure, Short Version/Details/Why It Matters, sign-off) still applies wherever a news-card format is used.

Masthead with brand emoji, tagline, issue number, lead headline, byline, Read Online | Unsubscribe → banner image → greeting → one POV thesis line → bulleted table of contents → dark divider bar → **six story cards** → utility segment that teaches something free → house blurb → Keep Reading strip → named sign-off → compliant footer with physical address and unsubscribe.

Each story card: small all-caps category label, emoji + headline as a link, image, then "The Short Version:" / "The Details:" bullets / "Why It Matters:", then "Read more →".

**Card 3 is always the house announcement, formatted byte-identically to the news cards.** Verify parity programmatically by diffing card style attributes — never by eye.

Mention budget: exactly 2 per issue (card 3 + the bottom blurb). Banned words: game-changing, unlock, revolutionize, imagine if, supercharge.

---

## FILE MAP

**Reorganized into folders on 2026-07-30.** Root holds only the core specs + whatever an active build is currently using.

Root: `CLAUDE.md`, `HANDOFF.md`, `NEWSLETTER-PLAYBOOK.md` (build spec incl. image rules), `OFFER-fractional-gtm.md` (current offer), `design-directions\` (the 3 finalized v2 templates: html-1-rundown / html-2-future-today / html-3-bold), `_send-to-singlebrain\` (active handoff outbox).

- `1-SENT\` — newsletters already emailed to a real list. Each: `<name>-issue-1\index.html` + `images\` + its `<NAME>-ISSUE-1.md` source.
- `ready-to-send\` — finished newsletters awaiting send, **each in its OWN self-contained folder** (index.html + `images\` + `medium-article.html/.md` + source `*-ISSUE-1.md` + `research\` + a ready `*.zip` for SingleBrain). E.g. `the-protocol\`, `the-people-person\`. New builds land here as their own folder; move to `1-SENT\` once emailed.
- `MISCELLANEOUS\` — outdated/superseded newsletter versions kept for reference.
- `research\` — `RESEARCH-*.md` (verified story candidates per niche; unused items reserved for later issues) + per-niche `research-*\` agent-output folders.
- `leads\` — master lead CSVs per niche + `lead-batches\` (sliced/deduped send lists).
- `medium\` — `medium-article-*.html` / `.md` + `medium-images-*\` (articles for pasting into Medium).
- `offers\` — offer flyer PDFs (the `OFFER-*.md` source stays at root).
- `deliverability\` — `DELIVERABILITY-*.md`. **Start with `DELIVERABILITY-FIX-PLAN.md` for anything deliverability-related** (live SPF/DKIM/DMARC + spam fixes).
- `docs\` — playbook-adjacent specs, concepts, Bird notes, the `listmonk-skill\` reference.
- `_archive\` — old zips. `_raw-assets\` — loose source images/logos.
- `newsletters\` — **the newsletter system**: `00-SOURCE-OF-TRUTH.md` (current strategy, structure, KPIs, footer rule, SMTP stack) + one spec per flagship (`main-street-affiliate.md`, `the-referral-channel.md`, `the-dealmaker.md`) + niche stubs (`niche-*.md`).
- `HANDOFF.md` — current state; update at the end of every session.
- Non-newsletter projects (`Overdeliver Mail Agency\`, `The Open Source\`) are left untouched.

---

## QUALITY STATUS — IMPORTANT

The current newsletter quality is **NOT locked in.** Xander has said explicitly that it is not there yet and will keep improving. This file, the playbook, and any skills built from them are **living documents** — update them as quality improves. Do not treat the current output as the final standard.
