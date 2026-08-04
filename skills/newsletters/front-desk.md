# Newsletter Skill — The Front Desk (gyms / fitness)

*Per-newsletter identity skill. Use with the general skills. The Front Desk is its OWN distinct publication — a pure-education gym-industry trade read. It no longer defines a shared template: the "locked Front Desk design for every niche" role is RETIRED (per the Aug 4 huddle — each newsletter now gets its own look + persona).*

## Mission & type
- **Type:** editorial / informational — a niche/industry trade publication.
- **Mission:** the trade read for people who **run gyms and fitness studios** — genuine industry news and operating intelligence, written like a real newsroom that knows the floor.
- **Job = trust, not conversion.** Industry/niche newsletters are **pure education and value — NOT an advert and NOT a link at the bottom.** Their only jobs are to build sender stats and earn reader trust. Conversion happens elsewhere (other publications / channels), never inside this one.
- **No offer. No pitch. No affiliate program.** Mention budget for this newsletter = **zero.**

## Identity
- **Brand:** The Front Desk
- **Niche:** gyms / fitness. Editorial, pure-education.
- **Byline:** Mara Ellison
- **From:** `The Front Desk <frontdesk@send.usingaitoscale.com>`
- **Reply-To:** `xander@usingaitoscale.com`
- **Subject:** on the gym-industry topic of the issue (current example: "The market's fuller than ever. Is your front desk ready?"). Keep it editorial — a gym-market angle, never an offer.
- **CTA:** none. No house CTA, no offer link, no "Read more →" to any of our properties. **No signup link** anywhere.
- **SMTP:** TBD — Justin owns sending (SendFox / ListMonk). Tell him what you need; don't assign it here.

## Format — editorial, pure education (NO offer)
Standard editorial flow, minus every commercial element:
1. Masthead (own logo + name + issue line) → warm "good-morning" intro → one POV thesis line → bulleted TOC → dark divider.
2. **Story cards — all genuine gym-industry news.** Each card keeps the craft: category label → emoji + headline (link to the real source) → image → "Image source:" caption → **The Short Version / The Details / Why It Matters** → "Read more →" (to the real third-party source).
3. Utility segment that teaches something free (an operator tip, a benchmark, a how-to).
4. Named sign-off (Mara Ellison) → clean footer.

**REMOVED for the pure-education model (this is the big content change):**
- ❌ **No native affiliate card at position 3.** That slot becomes a real gym-industry story like every other card. Nothing links to Medium or to our offer.
- ❌ **No bottom house blurb / CTA.** The issue ends on editorial value + the compliant footer — no ask.

So every card is real, browser-verified industry reporting. "Read more →" only ever points to the genuine source of that story.

## Design — its OWN look (universal-template role RETIRED)
- **The old rule is dead.** The Front Desk used to be the "locked template for all niches" (the Rundown-clone: black masthead + black section bars, gray `#f2f2f3` page, bronze `#9a5f1d` accent). That universal mandate is retired (`general/04-design-front-desk-template.md` no longer governs other newsletters). Treat those old specs as a *starting point to evolve away from*, not a lock.
- **Universal changes to apply next issue:**
  - **White background** (drop the gray page and the black-brown feel — white reads more professional).
  - **Wider layout** — move off the narrow centered ~600px column into a wider, more spacious layout.
  - **Its own logo** — a distinct Front Desk mark, not the generic shared one.
  - **Its own images** — a distinct gym-world visual feel; not the "canned / vintage / same-source" look. Different tool/platform if that's what it takes.
- **Keep the formatting craft** (Justin loves this — do NOT change it): the good-morning intro, bolds/italics, text blocks, the Short Version / Details / Why It Matters structure, quote blocks, image-as-format.
- **Own color identity.** Someone who receives two of our newsletters the same day should never guess they came from the same sender — The Front Desk's palette/type/logo must not echo The Dealmaker, The Referral Channel, or any other. Keep it simple; quality over quantity.

## Content
- **All cards = real, current, browser-verified gym-industry stories.** Sources used in the built issue: healthandfitness.org (×2), athletechnews.com. The former native card (position 3) must be replaced with a genuine story from a verified source — do not leave a promotional slot.
- Every stat/claim traces to a real fetched source (label vendor research as vendor research). If a number can't be verified, it doesn't ship.

## Compliance & build
- **No "AI Integraterz" / "Published by AI Integraterz"** anywhere. Footer = **The Front Desk** + physical address `37460 Beacon Brick Road, Zephyrhills, Florida 33541` + unsubscribe. **No socials. No signup link.**
- **Never** "power partner." No banned words (game-changing, unlock, revolutionize, imagine if, supercharge). No false relationship claims — this is cold outbound (never "you signed up").
- Email-safe HTML: **inline all CSS** (no `<head><style>` — clients strip it), ASCII/HTML entities only, merge tags `{{ MessageURL }}` / `{{ UnsubscribeURL }}`.
- Images: **Xander generates them** from text-safe prompts (SingleBrain never generates images).
- **Draft only; Xander approves before any send.**

## Status (2026-08-05)
Built earlier as the (now-retired) universal template. Folder: `ready-to-send/the-front-desk/` (index.html + images/s1–s4.jpg). **Not ready for the new direction.** Next issue needs a rebuild pass:
1. **Pure-education pass** — remove the position-3 native affiliate card and the bottom CTA/house blurb; replace the old card 3 with a real gym-industry story; zero offer touches.
2. **White background + wider layout.**
3. **Own logo + own gym-world images** (drop the shared/generic look).
Formatting craft stays; look + commercial model change.
