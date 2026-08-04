# SHARED RULES — Premium Newsletter Clones (v2)

You are building ONE premium email newsletter. Two other agents build the other two. **Quality is everything** — the last batch was rejected as "AI slop." These must look like a genuinely premium, real, professional newsletter — restrained and modern, not a generic "designed" template.

## NON-NEGOTIABLES
- **ZERO EMOJIS anywhere in the file.** Never at the start of a headline, sub-header, label, or bullet. Emoji-in-headers is the #1 AI tell. Not one emoji.
- **Faithful to your SPEC.** Match its colors, fonts, sizes, spacing, structure, and card styling as exactly as you can. This is a clone, not an interpretation. Do not add flourishes it doesn't call for.
- **Premium restraint.** Real typographic hierarchy, generous whitespace, clean rules. No decorative gradients, no rounded-everything, no cutesy touches. Simpler and cleaner wins.

## EMAIL-SAFE, SELF-CONTAINED HTML
- Table-based layout (`<table role="presentation" width="600" ...>`), 600px content width, centered on the page background.
- Core styling INLINE on every element. A `<style>` head block ONLY for one `@media (max-width:600px)` stacking rule.
- Web-safe font only: `Arial, 'Helvetica Neue', Helvetica, sans-serif`. NO Google/external fonts.
- NO external resources of any kind (no external image URLs, CSS, JS). Fully offline.
- **Image placeholders:** a FLAT solid light-grey block (`background:#e9eaec;`) at the slot's size, with one small centered muted label "IMAGE" (`#a1a1aa`, 12px). No gradients, no big captions. It should read as a clean empty photo area.
- No flexbox, no grid, no position:absolute. Tables + block elements only.
- Mobile: single column, fluid (`width:100%; max-width:600px`).

## BRANDING (placeholder — identical across all three)
- Newsletter name: **THE DISPATCH**
- Partner/sponsor name (where a spec needs one): **NORTHLINE**
- Footer company: **AI Integraterz · 37460 Beacon Brick Road, Zephyrhills, Florida 33541**

## CONTENT LIBRARY (use verbatim; pull the pieces your SPEC's structure needs; NO emojis)
- **Greeting:** Good morning. A permanent answer to the question that's hung over the industry for weeks finally arrived — and it reshapes how the fast movers operate from here.
- **Second intro line:** It's clarity for now, but likely not the last word — and it changes where this quarter's edge is hiding.
- **TOC (5 items):** The shift quietly redrawing the map / The one number nobody's talking about / THE DISPATCH opens something new / A team's counterintuitive win / A free tool you'll actually use
- **Story A — category TECHNOLOGY — headline: The Shift That's Quietly Redrawing the Map** — lead: The change most people missed is already deciding who wins the next 18 months. — bullets: "A concrete data point that grounds the claim and proves it's real." / "A second detail that shows the direction of travel." / "A third that explains why it's happening now, not last year." — why it matters: For anyone in the market, the window to move first is measured in weeks, not quarters.
- **Story B — category BUSINESS — headline: The One Number Nobody's Talking About** — lead: Buried in the latest figures is a metric that quietly predicts who pulls ahead. — bullets: "What the number is and where it came from." / "Why it's far higher than almost everyone assumed." — why it matters: It reframes the entire cost conversation for the year ahead.
- **Story C — HOUSE/NATIVE (style IDENTICAL to A and B) — category THE DISPATCH — headline: How THE DISPATCH Gets You There First** — lead: A new program built to put you in the room before your competitors know there's a room. — bullets: "The concrete thing it does for the reader." / "The proof point: what it delivered for the first cohort." — why it matters: It closes the exact gap the first two stories describe.
- **Sponsor block — category TOGETHER WITH NORTHLINE — headline: Ship Governed Apps Without Slowing Down** — body: Your team already builds fast; NORTHLINE keeps it compliant — auth, permissions, and audit logs built in. — bullets: "Generate production-ready apps from plain-language prompts." / "Run in the cloud or self-host for compliance." — CTA: Start building free
- **Quick hits — heading: Trending Tools** — items (link + em-dash + description): "Northline Studio — a governed app builder with drag-and-drop editing." / "Clearsignal — a new open-weights model for structured data." / "Cadence — calendar automation that respects focus time." / "Relay Live — a natural-sounding voice model for support teams."
- **Everything else — heading: Everything Else Today** — items (bold lead + text): "Pricing: a major player quietly changed its pricing, and the ripple is bigger than the headline." / "Hiring: demand turned positive for the first time in three quarters." / "Regulation: new rules take effect next month — here's the one line that matters."
- **Community — heading: How a Reader Is Using This** — body: Today's note comes from a reader in Austin. — quote: "I built a simple system that saves my team six hours a week — here's exactly how it works, step by step."
- **Utility / Prompt — heading: One free thing (Future Today label: PROMPT OF THE WEEK; headline: The Invisible-Work Audit)** — box copy: Describe your typical week and mark every task that (1) no one asked for, (2) no one would notice if it stopped, or (3) exists only because we've always done it. Rank them by hours reclaimed. Be blunt.
- **House blurb:** Quick note: THE DISPATCH helps teams get in the room before the brief goes out. Reply "IN" and we'll send details.
- **Ratings prompt:** That's it for today. What did you think of this issue? — options: Nailed it / Solid / Needs work
- **Sign-off:** See you soon, — The Editor, THE DISPATCH
- **Footer utility:** Update your email preferences or unsubscribe here. · © 2026 AI Integraterz · 37460 Beacon Brick Road, Zephyrhills, Florida 33541
