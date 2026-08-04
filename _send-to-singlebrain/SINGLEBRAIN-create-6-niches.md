# → SingleBrain: create the 6 niche newsletters (you do research + HTML + Medium)

*(Xander: paste this. SingleBrain does EVERYTHING — research, copy, HTML, Medium, image prompts. ONE newsletter at a time. No auto-send. Local Affiliate Pro is on hold.)*

## The 6 niche newsletters — Issue 001 each, ALL EDITORIAL
| Niche | Brand |
|---|---|
| Gyms / fitness | **The Front Desk** |
| Marketing / AI agencies | **Agency Insider** |
| Men's-health coaching | **The Protocol** |
| PR agencies | **The Green Room** |
| Recruiting / staffing | **The People Person** |
| Solar | **The Daily Sun** |

*(tech-B2B is dropped — that list is general, flagships only. men's-health-clinics: none, no leads.)*

## Format — editorial trade newsletter (value-first, NOT a sales pitch)
Masthead (brand + tagline + `No. 001` + a writer byline) → banner → greeting + one sharp POV thesis line → **exactly 4 story cards**:
- **3 are REAL news stories** — category label + headline linking to a **real, specific article** + image + `The Short Version:` / `The Details:` (4 **unique** bullets) / `Why It Matters:`
- **1 is the native affiliate card at position 3** — styled byte-identical to the news cards; `Read more →` points to the shared Medium article.
- **Every one of the 4 cards must have a real, valid source URL.**

→ utility segment (free, useful) → short house blurb + CTA → footer.

## ⚠️ CRITICAL RULES — last batch got these wrong, do NOT repeat
1. **Real sourced content only.** Every story = a specific real article + a concrete fact/number from it. **NO** templated/reused bullets, **NO** homepage or blog-index links, **NO** invented facts. If you can't find **3 real news stories** for a niche, STOP and tell us — do not ship filler.
2. **NO "AI Integraterz" anywhere.** The newsletter's **own name** is the company/brand.
   - House blurb: *"This is The Green Room. We build and run affiliate programs for businesses…"* — never "comes from AI Integraterz."
   - Footer: *"© 2026 The Green Room"* and "The Green Room" as the publisher line — **never** "AI Integraterz."
3. **A UNIQUE writer byline per newsletter** — a realistic first + last name, **different for each one** (do not reuse a single name across all). **List the name you assign to each** so Xander can approve.
4. **Editorial, value-first.** Real news that helps the reader. The offer shows up ONLY as the soft native card (1 of the 4) — not a pitch.
5. Offer = "affiliate program." **Never "power partner."**

## Medium
The native card's `Read more →` points to **ONE shared Medium article** (the affiliate-program explainer) for all 6 niches — reuse The Referral Channel's published one, or write ONE shared piece. **NOT one per niche.**

## Images
You can't generate images — **write labeled Higgsfield PROMPTS** per slot (banner + one per card). Photorealistic editorial, **text-safe: NO writable object in the scene** (no paper, notebooks, screens, signs). Banner = one prompt per newsletter. Xander generates them.

## Build + delivery
- No emoji. HTML entities. Exactly one hidden preheader div. Email-safe 600px tables, inline styles, ASCII-only.
- Byline = the unique writer name. From display-name = the newsletter's name. Reply-To `xander@usingaitoscale.com`.
- Footer = the newsletter's own name + physical address `37460 Beacon Brick Road, Zephyrhills, Florida 33541` + unsubscribe. **No social links.** Add a small secondary **"Subscribe" → `https://aware-quarry-prs5.here.now`** (Beehiiv opt-in).
- House-blurb CTA link: use `https://cal.com/usingaitoscale/aiintegraterz` for now unless Xander gives you a per-niche link.
- **ListMonk:** use a **BLANK / raw template** (whole body = `{{ template "content" . }}`, no wrapper, no border, no ListMonk footer) — our HTML is already a complete email. Host images via the **media API**. Merge tags `{{ MessageURL }}` / `{{ UnsubscribeURL }}`.
- **Deliver each as an actual `.html` file** (attach in Slack or email via `singlebrainslack@agentmail.to`) + its image prompts. Not pasted as chat text.
- **DO NOT auto-send anything.** Deliver the draft; **Xander reviews the ListMonk preview and gives the explicit GO before ANY send — including internal tests.**
- **ONE newsletter at a time**, with real research each. No batch production — that's what caused the slop.

## Update your skills
Bake in: niches are editorial; **no "AI Integraterz"** (newsletter-name IS the brand); **unique writer byline per newsletter**; ListMonk blank-template; no-auto-send / Xander-approves-preview.
