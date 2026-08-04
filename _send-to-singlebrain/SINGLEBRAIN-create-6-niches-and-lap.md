# → SingleBrain: create the 6 niche newsletters + Local Affiliate Pro (initial drafts)

*(Xander: paste this to SingleBrain. It creates the drafts — no auto-send. Work ONE newsletter at a time.)*

---

## CHANGES FROM TODAY'S MEETING — read first
1. **Niche newsletters are EDITORIAL** — straight news + genuine value, like The Referral Channel. **NOT** the direct-response sales-letter format (that's only The Dealmaker). Lead with real value; the offer appears **softly** as the disguised native card at position 3, not a hard pitch.
2. **tech-B2B is dropped** as a niche — that list turned out to be a general/mixed list, so it only receives the flagship newsletters, not a niche one. **No "Tech Stack" newsletter.** (Rename that list "general list.")
3. **men's-health-clinics: no newsletter** (no leads). The Protocol = men's-health **coaching** only for now.
4. **NEW newsletter: Local Affiliate Pro** (see §B).

## A) THE 6 NICHE NEWSLETTERS (editorial)
Create Issue 001 for each:
| Niche | Brand |
|---|---|
| Gyms / fitness | **The Front Desk** |
| Marketing / AI agencies | **Agency Insider** |
| Men's-health coaching | **The Protocol** |
| PR agencies | **The Green Room** |
| Recruiting / staffing | **The People Person** |
| Solar | **The Daily Sun** |

**Format (each — editorial, same as The Referral Channel):** masthead (brand + tagline + No. 001 + byline Jay Bell) → banner → greeting + one POV thesis line → **4–5 real news stories** (category label + headline linking to a REAL article + image + "The Short Version" / "The Details" (4 unique bullets) / "Why It Matters") → **native affiliate card at position 3** (styled byte-identical to the news cards; "Read more →" points to the shared Medium article — see §C) → a utility segment that teaches something free → short house blurb + CTA → footer.

**Hard content rule (anti-slop):** every story = a **real, specific article** + a **concrete fact/number** from it. NO reused/templated bullets, NO homepage or blog-index links, NO invented facts. **If you can't find 4 real stories for a niche, STOP and tell us — we'll supply verified research. Do not ship filler.** (This is exactly what went wrong last time.)

## B) LOCAL AFFILIATE PRO (new — promo roundup)
Justin's concept: a curated roundup of **hot affiliate offers/projects** for **local businesses**, positioning AI Integraterz as the local-affiliate connector — *"here are some hot offers that might be a good fit for your audience."* Domain: Local Affiliate Pro. Cadence 3×/week; audience = local businesses.

**Format:** masthead (Local Affiliate Pro + tagline + No. 001) → short intro → a numbered list of **~10 hot affiliate offers/programs** (each: name + one line on what it is + why a local business would want to promote/partner with it) → CTA: *"Want to see what else is selling? Let us know."* → footer. This one is more of a **deals roundup**, not editorial news.

**Offers must be REAL** — feature our own offer bank (Speaker Agent, Pinnacle Funding, The Affiliate Machine, ConnectMed) **plus** real, current, verifiable affiliate programs. No fabricated offers. *(Xander is confirming with Justin whether there's a specific offer list to use — build a first draft from real offers and flag any you're unsure of.)*

## C) MEDIUM ARTICLES
- The **editorial** newsletters (the 6 niches) each need their native card to point somewhere — use **ONE shared Medium article** (the affiliate-program explainer). Reuse The Referral Channel's published article, or write ONE clean shared piece. **Do NOT write a Medium article per niche.**
- The Dealmaker (direct) and Local Affiliate Pro do **not** need a Medium article.

## D) IMAGES
You can't generate images — **write labeled Higgsfield PROMPTS** for every image slot (one per filename: banner.jpg, s1.jpg …), following the standard: photorealistic editorial, **text-safe with NO writable object in the scene** (no paper/notebooks/screens/signs — the rule you just added), a different look per slot, banner = one prompt per newsletter. Xander generates them.

## E) RULES (all newsletters)
- Follow the playbook (rules 1–30) + the per-newsletter specs. Offer = "affiliate program" → CTA `https://cal.com/usingaitoscale/aiintegraterz`. **Never "power partner."**
- No emoji. HTML entities. Exactly one hidden preheader div. Email-safe 600px tables, inline styles, ASCII-only.
- Byline **Jay Bell**. From display-name = the newsletter's own name. Reply-To `xander@usingaitoscale.com`.
- Footer = the newsletter's own name + "Published by AI Integraterz" + `37460 Beacon Brick Road, Zephyrhills, Florida 33541` + unsubscribe. **No social links.** On the editorial niches, add a small secondary **"Subscribe" → `https://aware-quarry-prs5.here.now`** (Beehiiv opt-in). Not on Local Affiliate Pro.
- **Deliver each as an actual `.html` file** (attach in Slack or email via `singlebrainslack@agentmail.to`) + its image prompts. NOT pasted as chat text.
- **ListMonk loading:** use a **BLANK / raw template** whose whole body is just `{{ template "content" . }}` — no wrapper, no border, no ListMonk footer — because our HTML is already a complete email (the default template double-wraps it and draws a box). Host images via the **media API**. Merge tags = `{{ MessageURL }}` / `{{ UnsubscribeURL }}`.
- **DO NOT auto-send anything.** Deliver the drafts as files; **Xander reviews the ListMonk preview and gives the explicit go before ANY send — including internal tests.**
- **Work ONE newsletter at a time**, with real research each. Do NOT batch-produce all seven at once — that's what caused the slop. Quality over speed; a few done right beats seven hollow ones.

## F) UPDATE YOUR SKILLS
Bake in: niches are **editorial** (not promotion); tech-B2B dropped (general list, flagships only); the **ListMonk blank-template** rule; the **no-auto-send / Xander-approves-preview** gate.
