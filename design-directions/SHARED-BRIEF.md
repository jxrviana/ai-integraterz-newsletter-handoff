# SHARED BRIEF — 5 Newsletter Design Directions

You are building ONE email-safe HTML newsletter mockup that demonstrates a specific DESIGN DIRECTION. Four other agents are building the other four from this same brief. Everything EXCEPT the visual design must be identical across all five, so a human can compare the designs fairly and pick one.

## Hard rules
- **Work only inside the working directory.** Save your file exactly where your per-agent brief says.
- **Email-safe, self-contained HTML:**
  - Table-based layout (`<table role="presentation" ...>`), content width **max 600px**, centered on a page background.
  - Core styling **inline** on the elements (a `<style>` block in `<head>` is allowed only for a `@media (max-width:600px)` tweak and a `prefers-color-scheme` nicety — but the design must hold with inline styles alone).
  - **Web-safe font stacks only** — e.g. `Georgia, 'Times New Roman', serif` or `-apple-system, 'Segoe UI', Helvetica, Arial, sans-serif`. NO Google Fonts, NO external fonts.
  - **No external resources at all** — no external image URLs, no external CSS/JS. It must render fully offline.
  - **Image placeholders:** a solid-color or CSS-gradient block (via `background`/`bgcolor`), sized to the slot, with a small centered label like "BANNER IMAGE" / "STORY IMAGE". Tint the placeholder to suit your palette so it looks intentional. NEVER link an external image.
  - No flexbox, no CSS grid, no `position:absolute`. Tables + block elements only.
  - Must look **polished in a desktop browser** (the user judges it there) AND be structurally email-safe.
- **Mobile:** single column, fluid (`width:100%; max-width:600px`), holds up on a phone.

## Structure — same order for all 5
1. Hidden preheader text (the greeting line).
2. **Masthead** — brand "THE DISPATCH" with a small mark, the tagline, the issue line, and "Read Online · Unsubscribe".
3. **Banner image** placeholder (full width).
4. **Greeting + thesis line.**
5. **"In today's issue:" TOC** — the bulleted list.
6. A **divider**.
7. **Three story cards, identical visual treatment:** Card 1 (TREND), Card 2 (BY THE NUMBERS), **Card 3 = native house announcement (YOUR COMPANY)**.
   - **CRITICAL: Card 3 must be styled byte-identically to Cards 1 and 2** — same card style, headline weight, image slot, and bullet structure. It must read as another story, NOT an ad. This is the entire point of the format.
   - Each card: small all-caps category label · emoji + headline (as a link) · image placeholder · "The short version:" line · two bullets · "Why it matters:" line · "Read more →" link.
8. **Utility segment** — a "One free thing" value box. This is the ONE block allowed to look different from the story cards (a highlighted tip box).
9. **House blurb** — one short line.
10. **Sign-off** — "— The Editor".
11. **Footer** — company line + address + unsubscribe. Muted, small.

## EXACT content — use verbatim (only the DESIGN differs)
- Brand: **THE DISPATCH**
- Tagline: *The one-line promise your newsletter makes to its readers.*
- Issue line: **Issue #12 · January 15, 2026**
- Top links: **Read Online** · **Unsubscribe**
- Greeting: **Good morning.** Here's the one thing worth your full attention today — plus four more you'll want on your radar.
- Thesis: *The market rewards the few who move first. Here's where this week's edge is hiding.*
- TOC ("In today's issue:"): The shift quietly redrawing the map / The one number nobody's talking about / Your Company opens something new / A team's counterintuitive win / Plus: a free tool you'll actually use
- **Card 1** — label TREND · 📈 · headline **The Shift That's Quietly Redrawing the Map** · Short version: *One clean sentence summarizing the trend and why it's happening now.* · bullets: "A concrete data point that grounds the claim." / "A second detail that shows the direction of travel." · Why it matters: *One sentence connecting it to the reader's world.* · Read more →
- **Card 2** — label BY THE NUMBERS · 📊 · headline **The One Number Nobody's Talking About** · Short version: *One sentence on the surprising metric.* · bullets: "What the number is and where it came from." / "Why it's higher than everyone assumed." · Why it matters: *One sentence on the implication.* · Read more →
- **Card 3 (NATIVE HOUSE)** — label YOUR COMPANY · 🚀 · headline **How Your Company Gets You There First** · Short version: *One sentence describing the offer as if it were news.* · bullets: "The concrete thing it does for the reader." / "The proof point or result." · Why it matters: *One sentence on the reader benefit.* · Read more →
- **Utility** — heading **One free thing** · body: *A genuinely useful template, teardown, or tip the reader can act on today. Teaches something for free and asks for nothing — placeholder copy for the value-add block.*
- **House blurb:** **Quick note:** Your Company helps [audience] do [outcome]. Reply "IN" and we'll send details. →
- **Sign-off:** — The Editor
- **Footer:** **AI Integraterz · 37460 Beacon Brick Road, Zephyrhills, Florida 33541** / *You're receiving this because your work came up in our research. Unsubscribe · Update preferences.*

## Quality bar
Make it genuinely attractive and cohesive in your assigned design language — a real candidate for our house redesign, not a rough sketch. Spacing, hierarchy, and color must feel deliberate. The user picks ONE of the five, so make yours the one they want.
