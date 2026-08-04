# Outbound Newsletter Playbook
*Extracted from 3 reference newsletters Justin sent + his commentary · July 20, 2026*
*This is the build spec. Every issue we produce gets checked against it.*

---

## ⚠️ CRITICAL UPDATES (2026-07-29) — these OVERRIDE anything below that conflicts

Most of this playbook predates the design overhaul and the click-tracking fixes. Where they conflict, THESE win:

1. **NO EMOJIS anywhere** — not in the subject, masthead, headlines, or labels. Emojis are a top AI tell (Xander's directive) AND they render as `???` in some email clients (confirmed on Green Room). Ignore every "emoji + headline" instruction below; the masthead and subject lead with text only.
2. **Click tracking: JangoMail v2 API only.** Create the campaign via `POST /campaigns` with `tracking.click_track_html: True`, leave editorial links RAW, send via `PUT`. **NEVER manually wrap links through `/c.z`** — it breaks the links and doesn't track (it killed all 33 editorial links on the Jul 28 3,000-send). The pre-send gate must load one editorial link end-to-end to confirm it actually resolves. ListMonk tracks clicks natively.
3. **Encoding:** keep `<meta charset="utf-8">`; prefer HTML entities (`&mdash;` `&rsquo;` `&rarr;`) for special punctuation so nothing mojibakes downstream.
4. **Design system:** build from `design-directions/v2/` — `html-3` (Bold v2, locked primary), `html-1` (Rundown), `html-2` (Future-Today). Pick one per niche; recolor/rebrand per niche.
5. **Offer / native card:** the native announcement (card 3) + bottom blurb use the current offer in `OFFER-fractional-gtm.md` (Fractional GTM / embedded engineer; per-niche "win" — recruiting = placements). `{{OFFER_URL}}` / `{{MEDIUM_URL}}` = that niche's Medium article.
6. **Stack:** JangoMail (capped, resets ~Aug 2) → ListMonk via Resend SMTP → Bird secondary. AutoSend cut. Current state always lives in `HANDOFF.md`.
7. **Medium/blog articles ship as paste-ready HTML, never just markdown.** Deliver every article as a self-contained HTML file (base64-embedded images, styled headings and links) matching `medium-article-mens-health-coaching.html`, so Xander pastes it into Medium with formatting intact. The `.md` is an intermediate draft, never the deliverable.
8. **Real logo, real byline.** The masthead uses a generated logo emblem beside the wordmark — never a letter tile like "PP". The byline is a real-sounding sender name, not an obvious persona (The People Person = Jay Bell).
9. **Image quality — Xander's standing complaint (see §8).** Newsletter images must read as REAL editorial/news photographs — specific, textured, alive, photojournalistic, natural light — the kind that runs in an actual news article. NOT generic, clean, sterile, minimal, or stock-like; that reads as "AI slop" and gets rejected. Model stays GPT Image 2; the lever is PROMPT QUALITY. Keep text-safety, but choose text-safe subjects that are still vivid and news-like, not empty sterile still-lifes.
10. **Seed every send list with `xander@usingaitoscale.com` AND `justin@usingaitoscale.com`** (Justin, Jul 29) — they must receive the exact copy that goes to the leads, on every send.
11. **From display-name = the newsletter's name** (e.g. "The People Person"), never the bare address. The address stays on `send.usingaitoscale.com`.
12. **Deliverability is the priority — track bounces, opens, clicks, and open/click-tracking on every send** (Justin, Jul 29). The tracking pixel and link-wrapping can themselves affect deliverability, so watch them. Primary sender = ListMonk (native click tracking); JangoMail stays v2-only for side-by-side testing.

**— Added 2026-07-30:**

13. **Build OUTPUT = a self-contained folder under `ready-to-send/<newsletter>/`** — `index.html` + `images/` + `medium-article.html/.md` + the source `*-ISSUE-1.md` + `research/` + a ready `*.zip` for SingleBrain. The zip = `index.html` + `images/` EXCLUDING `images/masters/` (raw PNGs stay local). Move the folder to `1-SENT/` once emailed; superseded versions → `MISCELLANEOUS/`.
14. **CTA link per niche** (see `offers/CTA-LINKS-BY-NICHE.md`): coaches/experts → `https://aiintegraterz.com/unreplaceable-expert`; operators (clinics, recruiting, solar, HVAC) → `https://aiintegraterz.com/blueprint`; `/sovereign` = reserved operator variant. (Green Room is the exception — it advertises SpeakerAgent, not these.)
15. **Card-3 native-ad wiring:** card 3's "Read more →" points to the niche's **Medium article** (`{{MEDIUM_URL}}`), exactly like the news cards point to their sources. The **offer-page button** (`/blueprint` etc.) lives ONLY on the **bottom house blurb** (and inside the Medium article) — NEVER as a button on card 3, or it breaks card 3's byte-parity and blows its native-ad cover.
16. **Reply-To on every campaign = `xander@usingaitoscale.com`.** `send.usingaitoscale.com` is send-only (no inbox); without a Reply-To, reader replies — the booked-call signal — vanish.
17. **Medium article top CTA (future issues):** after the TL;DR/subtitle, add a non-salesy "Read more here" link to the niche's offer page — ONLY if it doesn't hurt the article's quality (skip if it reads salesy). Xander's Medium publishes 1/day; after publishing, resolve `{{MEDIUM_URL}}` to the live URL in the newsletter.
18. **Sending stack (current):** Resend (primary, via ListMonk) is on the FREE tier (~100/day, ~3,000/mo) — the paid upgrade is **admin-only = Justin** and gates real volume. **Bird (backup) stays DISABLED — enable only on explicit instruction** (ListMonk round-robins across all enabled SMTP servers). Bird SMTP = `us1.smtp.bird.com:587` STARTTLS, user `bird`, password = a Bird API key with the `emails` scope; in Bird's SMTP config set Category = **Marketing** + Track opens/clicks **OFF** (ListMonk owns tracking).
19. **JangoMail large batches:** create a JangoMail group → CSV-import recipients → **SendMassEmail** (v2, `click_track_html: true`). Do NOT use v2 `to_other` for batches — it hard-caps (~9 recipients) AND still burns the full remaining credit allotment.
20. **Lead hygiene — send only to VERIFIED-deliverable leads.** Clean masters live in `leads/clean/` (filter = valid email + SmartLead `current_seq_num >= 1` + `is_bounced != true` + not `BLOCKED` + not `got_reply` + deduped). A niche with `current_seq_num = 0` across the board is UNVERIFIED — it needs a verification pass before any send. Never blast unverified leads (accept-alls / bad addresses = bounces = reputation damage).
21. **Byline = `Jay Bell` (standard across all newsletters)** — it reads as Justin Bell's pen name, so it's never a fabricated persona; do not invent a new name per issue. The masthead brand mark = a small real logo image (`images/logo.png`), never the emoji character.
22. **Build pipeline = multi-agent (Opus 4.8 subagents):** Stage 1 research (parallel agents, source-verified) → Stage 2 copy (one agent, against this playbook) → Stage 3 production (HTML + Medium + images IN PARALLEL). HTML/Medium/images can't start until the copy exists. Claude orchestrates + QA's (stat-trace every card, card-3 byte-parity check, link/placeholder check, render check).

23. **Every Medium article ships with 5 Medium tags.** Always hand Xander 5 relevant Medium tags/topics with each Medium-article deliverable — he adds them at publish and shouldn't have to ask (Xander, 2026-07-31).

24. **Never say "power partner" / "power partners" in customer-facing copy — the offer is an "affiliate program."** Retired 2026-07-31 (the jargon isn't clear on first read). Say "affiliate program," "affiliates," "referral partners," or plain "partners." Amber Spears' cited "Power of Eight" framework is fine (attributed editorial reference, not our offer name). *(This bans the term in OFFER copy. It is allowed as an internal newsletter angle/name — e.g. The Dealmaker's JV/power-partner angle.)*

25. **Footer — NO social links; brand to the newsletter's own name (Justin, Aug 1).** Remove LinkedIn/YouTube/Skool from the footer of outbound issues: extra links split traffic away from the offer, Justin's personal LinkedIn creates a footprint across 100k+ sends, and it can trip spam filters. The footer's visible brand = the **newsletter's name** (e.g. "The Dealmaker"), NOT "AI Integraterz"; keep the compliant legal line (*"Published by AI Integraterz"* + physical address + unsubscribe) for CAN-SPAM. Social links only when specifically useful/tested (e.g. one "Connect with me on LinkedIn" line in the signature). *(Reverses the Jul-31 add.)*

26. **Two registers — editorial vs direct-response.** The six-card news format in §5 is the EDITORIAL register (The Referral Channel + the niche newsletters). The direct-response flagships (Main Street Affiliate, The Dealmaker) are a persuasive **letter** (opener → reframe → offer → proof → do-it-Monday play → CTA), NOT news cards — but the same discipline applies (verified stats only, no hype/spam density, no emoji, HTML entities, exactly one hidden preheader div, seed the send, Reply-To). Editorial-vs-direct is itself an ongoing split-test.

27. **KPI targets + split-testing (Justin, Aug 1 — full detail in `newsletters/00-SOURCE-OF-TRUTH.md`).** Targets: **30% opens** (deliverability → primary inbox, subject line, preview text), **10% click rate** (quality, relevance, clear CTA), **≥1 booked call per send**. Test twice as much as you send: a **control + 2–3 variants**, same list at **different times** (swap them day-to-day), and a **plain-text "Sendiva-style"** variant against the designed one.

28. **Offer = the affiliate program (`offers/OFFER-affiliate-program.md`) — supersedes the fractional-GTM offer in rules 5/14/15.** CTA destination = `cal.com/usingaitoscale/aiintegraterz` (fallback) or `mainstreetaffiliate.com` (when live). Niche card-3 CTAs point here too. The native-card mechanic (rule 15) is unchanged — only the destination/offer changed. **NEVER brand it "power partner"** (rule 24).

29. **Editorial issues: AT LEAST 4 news stories (5 preferred) + the native house card at position 3 (Xander, Aug 3).** Never ship 2–3 news stories — it reads too thin. The house/native card sits in the **MIDDLE of the run (position 3), never last.** Direct-response letters (The Dealmaker) are exempt from the card count, but still need **concrete, specific, sourced substance** — real numbers and real findings, never hedged "research shows…" generalities.

30. **Every story must carry REAL, SPECIFIC facts from a REAL article (Xander, Aug 3 — anti-slop).** Banned: identical/templated "Details" bullets reused across cards; vague "the source describes a market change" filler; linking to a homepage or blog index instead of a specific article. If a story has no specific, sourced fact, it does not go in the issue. Volume never justifies hollow copy — this is exactly the "AI slop" Justin rejects.

---

## 0. Justin's directive — the most important line

On the MyClaw issue he forwarded:

> *"Notice that the third one down is an announcement about their business with managed Hermes but it looks like another article. They've had that feature. They just plugged it in there to get more clicks through to their site. **We want to do the exact same**."*

**Decoded:** MyClaw's story #3, "MyClaw Adds Managed Hermes Hosting," is styled **identically** to the real news stories around it — same headline weight, same image, same `TL;DR:` opener, same `Read more →` link. No "sponsored" label. No tonal shift. A reader scanning the issue processes it as the third news item of the day. It isn't even new ("they've had that feature") — it was inserted to drive clicks to their site.

**Three rules that follow:**
1. **The house item is a STORY, not a pitch.** Same format as every other block, zero deviation.
2. **It sits in the middle of the run** (position 3 of ~7), never last. Last = ad position. Middle = editorial position.
3. **It doesn't need to be news.** Any real capability, offer, result, or asset can be written up as an announcement.

---

## 1. The three references

| # | Newsletter | Publisher | Cadence | Format identity |
|---|---|---|---|---|
| A | **MyClaw Newsletter** | MyClaw (AI agent platform) | Daily | Pure TLDR clone. 6–7 stories, image each, `TL;DR:` + `Read more →`. Own product inserted as story #3. |
| B | **The Future Today** | Forward Future (Matthew Berman, Nick Wentz) | Daily | Magazine. Labeled sections, bordered cards, video embed, prompt segment, feedback buttons, named humans. |
| C | **There's An AI For That** | TAAFT | Weekly | Marketplace digest. Sponsor banner up top, TOC bullets, numbered tool lists, prompt-of-week, star-rating feedback. |
| D | **The Rundown AI** | The Rundown (Vancouver) | Daily | **The most rigorous of the four.** Boxed cards, black section-divider bars, a fixed 3-part story formula, tutorial slot, reader-community slot, team photos. 2,000,000+ subscribers. |

### D deserves its own breakdown — the 3-part story formula

Every Rundown story runs the identical skeleton, and it's the single best pattern in all four references:

> **[CATEGORY LABEL]** *(tiny grey caps: ANTHROPIC · AI TRAINING · OPENAI)*
> 🔸 **Headline as an underlined blue link**
> *[image]* — with an `Image source:` caption
>
> **The Rundown:** one paragraph — what happened, plainly.
> **The details:** 3–4 bullets — the specifics, each with a linked source word.
> **Why it matters:** one paragraph — the analysis. What this changes for the reader.

Why it beats a plain `TL;DR:` — the reader gets *news + evidence + interpretation* in a fixed rhythm. "Why it matters" is where the publication earns authority, and it's the slot where a house POV lives legitimately. **Adopt this as our default story block.**

Other Rundown-specific steals:
- **Black divider bars** naming each act: `LATEST DEVELOPMENTS` → `QUICK HITS` → `COMMUNITY`.
- **Boxed intro** with a real 2-paragraph editorial take, then **"In today's rundown:"** + 5-bullet TOC.
- **Labeled ad slots** (`TOGETHER WITH RETOOL`, `PRESENTED BY OUTREACH`) that still use the house story formula — so they read native *even while disclosed*. Note the contrast with MyClaw's undisclosed insert; both work, disclosure is the safer default.
- **Tutorial slot** — "Deploy a mini-SaaS in minutes," with `Step-by-step:` numbered instructions and a `Pro tip:`. Pure utility.
- **Community slot** — a real reader's workflow, quoted, with name and city, ending "How do you use AI? Tell us here." Manufactures belonging and generates replies.
- **Cross-promo strip** — links to their other newsletters and next event.
- **"Was this email forwarded to you? Sign up here"** — the growth loop.
- **Team photos + first names** at the sign-off: "Rowan, Zach, Shubham, and Jennifer — the humans behind The Rundown."

All three are **free, ad/product-supported, curation-first**. None of them read as sales emails. That's the whole trick.

---

## 2. Anatomy comparison

| Slot | A · MyClaw | B · Future Today | C · TAAFT |
|---|---|---|---|
| **Subject** | 🦞 + lead headline | — | — |
| **Preheader** | "Plus: [2 other stories]" | "Plus: today's prompt…" | — |
| **Top bar** | — | Date · Read online | Date · Read online |
| **Masthead** | Emoji + lead headline as issue title, byline, Read Online \| Unsubscribe | Black block wordmark | Display wordmark |
| **Banner** | Branded mascot banner w/ tagline | — | **Sponsor ad banner** |
| **Greeting** | "Good Morning, Agent Owners!" | "Good morning. It's Monday, July 20, and we're covering…" | "Hey, Justin!" + "#1 AI newsletter on the planet" |
| **Thesis line** | ✅ One sharp POV line | Rolled into intro | — |
| **TOC** | — | Intro names 3 topics | ✅ **7 teaser bullets** |
| **Stories** | 6–7 blocks: headline · image · `TL;DR:` · `Read more →` | Grouped rollup + individual bordered cards w/ section labels | Themed sections, emoji-led links |
| **House/sponsor** | **Story #3, disguised** + bottom blurb + branded image | "Partner With Us" in footer | Top banner + mid advertorial + 2 "become a sponsor" asks |
| **Utility segment** | — | ✅ Prompt of the Week (copyable) | ✅ Prompt of the Week + Tools of the Week (10, numbered) |
| **Feedback** | 👍 More like this / 👎 Less like this | 3 buttons + "We read every response" | 4 star-rated options |
| **Recirculation** | ✅ Keep Reading — 3 past issues w/ thumbnails | — | — |
| **Sign-off** | — | ✅ Named humans | ✅ Brand + socials |
| **Footer** | © + Unsubscribe | Socials + partner ask | **Gmail Primary-tab request** + preference center + privacy |

---

## 3. The 15 patterns worth stealing

### Structure
1. **Lead story becomes the issue title.** MyClaw's masthead headline *is* story #1. One headline does double duty — subject line, masthead, first block.
2. **Emoji + headline subject line.** `🦞 Agent Swarm Breaches Hugging Face`. The emoji is a brand marker in a crowded inbox — same one every issue.
3. **"Plus:" preheader.** Subject carries the lead; preview text lists 2 other stories. Two hooks for the price of one.
4. **A one-line thesis after the greeting.** MyClaw: *"Autonomy is accelerating everywhere except inside the companies paying for it."* One sentence of POV that frames the whole issue. Cheap to write, makes the issue feel edited rather than assembled.
5. **TOC bullets for long issues** (TAAFT). 5–7 bullets of what's inside. Buys scannability and sets expectations.
6. **Section labels** (Future Today): small caps color labels — `MARKET PULSE`, `INFRASTRUCTURE`, `REGULATION`. Turns a list into a publication.

### The money mechanics
7. **The native announcement** — §0. Non-negotiable, position 3.
8. **Bottom house blurb.** After the stories: 2–3 plain lines on what the company is + one CTA line. MyClaw pairs it with a second branded image. This is the *second* mention — the native story was the first. Two touches per issue, no more.
9. **A recurring utility segment.** Prompt of the Week / Tools of the Week. Pure give, zero ask, and it's the thing people forward. Cheap to produce, builds the habit.
10. **Numbered lists** (TAAFT's 10 tools). Fastest-to-produce, highest-scannability block in any of these. Emoji + bold linked name + one line.

### Engagement + deliverability
11. **Feedback widget at the end.** All three have one. Two jobs: signal for us, and a *click* — engagement that inbox providers read as "this person wants this mail."
12. **Recirculation strip** (Keep Reading). 3 past issues w/ thumbnails + "Plus:" sublines. Free extra clicks, and it makes issue #1 look like issue #40 — we can seed it with our own source links until we have back issues.
13. **The Gmail Primary-tab ask** (TAAFT footer): *"If you want to keep receiving our updates seamlessly, it's crucial to move our emails into your Primary tab."* A direct deliverability tactic — a reader who does this permanently improves placement.
14. **Friendly preference exit.** TAAFT: *"Too frequent? Update your preference here"* before *"Unsubscribe here."* Offering a downgrade catches people who'd otherwise hit spam. Complaint-rate insurance.
15. **Named human sign-off** (Future Today: "— Matthew Berman, Nick Wentz & the Forward Future Team"). A person, not a brand, makes replies feel possible — and replies are our lead mechanism.

---

## 4. Copy rules observed (all three)

- **Story summaries are 55–85 words.** Subject-first, factual, no adjectives of excitement: *"Hugging Face says an autonomous AI agent swarm breached its dataset-processing pipeline, exploited two code-execution flaws, stole internal credentials, and performed more than 17,000 actions…"*
- **Numbers carry the weight.** 17,000 actions. 27,500 GPUs. $188B valuation. Specificity *is* the credibility.
- **Zero hype vocabulary.** No "game-changing," no "revolutionary," no "imagine if." The news is the news.
- **The house item uses the same register.** MyClaw's own announcement reads as flatly as the Hugging Face breach.
- **One idea per paragraph, 1–3 sentences.** Mobile-first throughout.
- **The reader is addressed as an operator**, never as a "subscriber" or "friend."

---

### Spam-word discipline (added 2026-07-24)

Justin's instruction: avoid spam trigger words. Scan every issue before it ships.

**Words to avoid or minimise:** buy · cash · money · sale · promotion · free · discount · cheap · earn · income · profit · guarantee · act now · limited time · urgent · click here · order now · special offer · risk-free · no obligation · winner · congratulations · miracle · amazing · 100% · credit card

**The rule is minimise, not ban.** These newsletters report on business and money, so some of these words are unavoidable and legitimate — "Cash and short-term investments $751 million" is financial reporting, not spam. What actually reads as spam is the *density and the register*: sales language in a sales context. News language in a news context is fine.

**What to fix on sight:**
- Category labels — never use `MONEY`. Use `MONETIZATION`, `REVENUE`, or `ECONOMICS`.
- Two spam words adjacent (e.g. "free cash flow") — rewrite or cut, that pairing is the strongest signal.
- The same word twice within a few lines — vary one.
- Our own copy (utility segment, house blurb) — we control this entirely, so it should be clean. Sourced story copy gets more latitude because rewriting it risks accuracy.

**How to scan:** strip HTML tags, decode entities, regex the list above with word boundaries against the visible text, and print surrounding context — a bare count is useless because context decides whether a hit matters.

**Honest weighting:** keyword filtering is a much smaller lever than SPF/DKIM/DMARC authentication, sender reputation, and engagement. Do this because it is free, not because it is the main defence. The bigger content risk is inherent niche vocabulary — a men's-health newsletter necessarily contains "testosterone," "hormone," "peptide," and "prescription," and no wordsmithing removes that. Those issues need the strongest authentication and the slowest volume ramp.

## 5. Our house format v2 (build from this)

```
SUBJECT     [emoji] + lead story headline           ← same emoji every issue
PREHEADER   Plus: [story 2], [story 3]

MASTHEAD    [emoji] NEWSLETTER NAME
            Tagline · Issue # · Lead headline · Byline · Read Online | Unsubscribe
BANNER      Branded banner (not a story image)

GREETING    "Good morning, [audience noun]."
THESIS      One sharp POV line framing the issue

STORY 1     Category label · emoji + linked headline · image · body · Read more →
STORY 2     "
STORY 3     ★ THE NATIVE ANNOUNCEMENT — identical formatting, links to our source
STORY 4     "
STORY 5     "
STORY 6     "

UTILITY     Recurring give (method / tool list / playbook / benchmark)
HOUSE       2–3 line blurb + single CTA          ← second and final mention
KEEP READING  3 teasers w/ "Plus:" sublines
SIGN-OFF    Named human
FOOTER      Company · physical address · Primary-tab ask · preference link · unsubscribe
```

**SIX cards: five real news stories plus the house announcement at position 3.** Earlier versions of this playbook said five — that was wrong and contradicted every shipped issue.

**Mention budget: exactly 2** (native story + house blurb). One is a wasted send; three is an ad.

### Canonical story labels — settle this before drafting

Three variants shipped, which is one too many. **The standard going forward is:**

> **The Short Version:** one paragraph, 40–70 words — what happened, plainly.
> **The Details:** four bullets, each a specific sourced fact.
> **Why It Matters:** one paragraph, 40–70 words — what this changes for the reader. Our POV lives here.

**Do NOT use "The Rundown:"** — that is the masthead of an actual publication (The Rundown AI) and borrowing it as a section label is sloppy. *The Protocol* and *The Green Room* shipped with it before this was settled; correct them at issue #2 rather than mid-flight.

**The `TL;DR:` single-paragraph fallback** is legitimate when the research only supports a summary and detail bullets would have to be invented. *The People Person* uses it for exactly that reason. **A format upgrade never justifies unsourced copy.**

**Feedback widget (👍/👎):** present in all four reference newsletters and worth having, but it needs two tracked URLs to be measurable. Removed from all three send-ready issues rather than blocking the first send. **Optional, not a gate** — restore when tracked links exist.

**Images: eight per issue** — banner (s0), one per story card (s1–s6), one for the utility segment (s7).

---

## 6. Case file — how *The People Person* Issue #1 was brought into spec

Issue #1 was built before Justin's directive and violated it in four ways. **All four are now fixed** (2026-07-21); this section is kept as the worked example of what "pre-directive" looks like, because the next niche will drift the same way if nobody checks.

| Defect found in audit | Fix applied |
|---|---|
| House content sat at **position 6 (last)** — the ad slot | Moved to **position 3**, category label `PARTNER NETWORK` |
| It was a **teaching essay** — no `TL;DR:`, no `Read more →`, and **no hyperlink of any kind**, so it drove zero clicks | Rewritten as an announcement using the identical block skeleton. Story headlines were also made clickable (previously only "Read more" was, halving click surface) |
| The 3-channel teaching was doing double duty as the ad | Kept, but moved to the **utility segment** after story 6 — it's genuinely good content, it just isn't the native ad |
| Missing thesis line, TOC, feedback widget, Primary-tab ask, preference link, named sign-off | All added |

**Verification that matters:** format parity was confirmed by extracting the tag skeleton and every `style` attribute from all six cards and diffing them — cards 2–6 byte-identical to card 1. Do this programmatically; the human eye will not catch a 2px padding difference, and that difference is what tells a reader "this one is an ad."

**Standing lesson — sourcing beats format.** The rebuild was told to adopt the 3-part *Rundown* skeleton, but the existing stories only ever had `TL;DR:` paragraphs; converting them would have meant inventing "The details" bullets and "Why it matters" analysis no source supported. It correctly kept `TL;DR:` throughout instead. **A format upgrade never justifies unsourced copy** — if a niche's stories need the 3-part skeleton, that's a research pass, not a rewrite pass.

**Still blocking a real send (both issues):** `{{OFFER_URL}}` — the destination the whole native-announcement play exists to drive clicks toward. Justin owes us this.

---

## 7. Production checklist (per issue)

- [ ] Subject = emoji + lead headline, under 55 chars
- [ ] Preheader = "Plus: …" naming 2 other stories
- [ ] 5 real news stories + the house announcement at position 3 = **6 cards**, every stat traced to a fetched source
- [ ] Native announcement at position 3, indistinguishable in format
- [ ] Utility segment included
- [ ] Exactly 2 house mentions
- [ ] Feedback widget + Keep Reading strip
- [ ] Named sign-off
- [ ] Footer: address, unsubscribe, preference option, Primary-tab ask
- [ ] Zero hype words; every paragraph 1–3 sentences
- [ ] Spam-word scan run (see §4) — no `MONEY` label, no adjacent trigger pairs, our own copy clean
- [ ] Preheader div carries **no near-zero `font-size`** and **no `color:transparent`**. Use exactly: `<div style="display:none;max-height:0px;overflow:hidden;mso-hide:all;">` — nothing else. A `font-size:1px` here triggers SpamAssassin's `__FONT_INVIS` (verified against the rule source), which cost 2.499 points on mail-tester and arms six sibling rules worth 2.5–3.5 each. Colour-matching-the-background is a *different, near-worthless* rule (`HTML_FONT_LOW_CONTRAST`, 0.001) — do not confuse them.
- [ ] Exactly ONE hidden element per email (`display:none` feeds `__STY_INVIS`; harmless once, risky repeated)
- [ ] Images: one per story block, consistent style set

---

## 8. Image production — hard-won rules

**THE BAR (Xander, reaffirmed 2026-07-29):** images must look like real **news/editorial photographs** — a photo you'd see illustrating an actual article — specific, textured, alive, natural light and honest imperfection. Generic, clean, minimal, sterile, or stock-like shots read as "AI slop" and get rejected on sight. Keep using **GPT Image 2** (Xander's model choice), but the fix is **prompt quality**: describe a real scene with real, lived-in detail, not a staged still-life. Text-safe AND vivid — not empty.

The first two image sets were rejected by the client as *"templated, cheap, AI slop."* The cause was a **locked style block** — one palette, flat-vector, one model across every slot. Real newsletters look like curated news precisely because every image came from somewhere different. These rules are what fixed it, learned across five sets and ~180 credits.

### The brief
- **Photorealistic editorial/press photography only.** Never illustration, vector, 3D render, or infographic.
- **A different model per slot** — this is the single biggest variety lever. No model more than twice per issue.
- **Vary lighting, colour temperature, composition, focal length and mood per image.** Write it into the brief as: *if any two images look like the same shoot, you failed.*
- **Art-direct each slot independently.** Never write a reusable style block.
- **Never brief two slots with the same subject.** This mistake was made twice (two van scenes in HVAC; two empty-studio-with-chairs in the podcast set) and cost two re-shoots. Read the eight directions together before sending.
- **Exception to the variety rule:** the house/native-ad image must NOT be the visual outlier. It has to sit naturally among the news images or it flags the block as an ad.

### Model behaviour (verified across five runs)
| Model | Behaviour |
|---|---|
| `gpt_image_2` | **Defaults to `quality:"low"` — always force `high` + `2k`.** This default is the likeliest root cause of the original "cheap" complaint. |
| `nano_banana_pro` | **Silently aliased server-side to `nano_banana_2`.** You cannot get the Pro tier; plan rotation accordingly. |
| `flux_2` (pro) | Best constraint-following. Defaults to 1k — force the tier. |
| `cinematic_studio_2_5` | Reliable, 4k. **Ignores time-of-day unless it is the FIRST thing in the prompt, in caps** ("NIGHT HAS FALLEN"). Cost two daylight misses before this was found. |
| `soul_2` | Best film grain, but **ignored explicit negative instructions three times running.** Use for texture, not for scenes with things that must be excluded. |
| `seedream_v4_5` / `v5_pro`, `kling_omni_image`, `nano_banana_2` | Solid all-rounders. |

### The text problem — the biggest tell
Garbled AI lettering is what makes an image read as fake. A "no text" clause in the prompt is **not sufficient**. The real rule:

> **Choose concepts where no surface in frame could plausibly carry lettering.**

Some concepts are *structurally* text-generating and no prompt discipline saves them. A windshield POV failed twice because it frames a car interior (warning labels, gauges, head-unit buttons) *and* a street (signage) simultaneously. Also high-risk: whiteboards, equipment with badges, vehicles with grilles or livery, product packaging, book spines, screens, notebooks, building facades.
**Safe subjects:** lawns, sky, bare ground, asphalt, fabric, foliage, coiled cable, empty rooms, unbranded tools, water, food, hands.
The strongest images in all five sets were the emptiest ones — an attic, a hearing room, a marble café table.

### Verification
- **Look at the images.** Use `Read` on the .jpg — do not trust an agent's self-report.
- Inspect masters at full size, then zoom the text-capable surfaces specifically.
- A surviving small label can be patched by cloning adjacent texture — but that is a **hand edit and must be disclosed**, not passed off as a generation.
- Check the delivery size, not the master: defects invisible at 600px do not matter, and masters can keep them.

### Delivery specs
600px wide, JPEG quality 62, ~140–215 KB total for eight images. Keep .png masters alongside for future re-use. The HTML must declare `width="594"` on story images and `width="600"` on the banner — **never declare larger than the source** or the client upscales it.

## 9. Source examples on file
- **A** — MyClaw, *"🦞 Agent Swarm Breaches Hugging Face,"* Jul 20 2026 (+ *"Agent Runs Mom's Business,"* Jul 17)
- **B** — Forward Future, *"The Future Today,"* Jul 20 2026
- **C** — TAAFT, *"There's An AI For That,"* Jul 19 2026
