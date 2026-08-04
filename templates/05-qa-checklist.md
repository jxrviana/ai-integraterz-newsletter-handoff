# Stage 5 — Pre-Handoff QA Checklist

**Placeholders: none.** This file is used as-is. Where a command shows a path, substitute the issue you are checking. Run this after stage 4 and before anything goes to the ESP, the client, or a test send.

Run it top to bottom. **Every item needs a method, not an opinion** — "looks fine" is not a result. Twelve checks; any single failure blocks handoff.

Two files you are checking against throughout: the issue markdown (`<NAME>-ISSUE-N.md`) and the built HTML (`<name>-issue-N\index.html`).

---

### 1. Every statistic traces to a fetched source

- [ ] Every number, date, percentage, dollar figure and quoted phrase in the HTML appears in the research file, attached to a URL that was fetched.

**Method:** Take the Sources table from the issue markdown. For each card, read the card in the HTML and tick each number off against the matching research entry. Any number in the HTML that is not in the research file is a fabrication — cut it or source it. Pay particular attention to numbers that appear in the thesis line, the TOC bullets, and the Keep Reading sublines, because those are written last and are the ones that drift.

- [ ] Every source the research file flagged **Secondary** is still flagged in the issue's Sources table, and nothing presented as primary is actually secondary.

---

### 2. Card 3 parity, verified programmatically

- [ ] Every `style` attribute across all six story cards diffs clean against card 1.

**Method:** Extract the tag skeleton and every `style` attribute from the six story-card table rows, in document order, and diff cards 2-6 against card 1. Read the diff output. The only permitted differences are text content, `href`, image `src` and `alt`.

**Do not do this by eye.** A 2px padding difference is invisible to a human and is exactly the signal that tells a reader card 3 is an ad.

- [ ] Card 3 also passes the reading test: same category-label style, same emoji weight, same three-part body, same `Read more →`, no "sponsored" label, no second person, no adjectives of excitement.

---

### 3. All images resolve and are the right ones

- [ ] Eight JPEGs exist in the `images` folder beside the HTML: `s0.jpg` through `s7.jpg`.
- [ ] Every `<img src>` in the HTML points at a file that exists.
- [ ] Opening the HTML in a browser shows eight images, none broken.

**Method:** List the images folder, then grep the HTML for `img src=` and compare the two lists. Then actually open the file in a browser and scroll it. Then `Read` at least the banner and the s3 house image to confirm they are what the brief asked for — an agent's self-report is not evidence.

- [ ] No image declares a width larger than its source (600 banner, 594 story and utility).
- [ ] Every image has literal alt text. None empty, none generic, none a filename.

---

### 4. Placeholder inventory

- [ ] The only tokens left in the HTML are `{{UNSUBSCRIBE_LINK}}` and `{{VIEW_ONLINE_LINK}}`.

**Method:** Grep the HTML for `{{` and count occurrences of each distinct token. Expected placements: `{{UNSUBSCRIBE_LINK}}` in the top bar and the footer; `{{VIEW_ONLINE_LINK}}` in the top bar and the footer preferences line.

- [ ] `{{OFFER_URL}}` is resolved to a live destination. If it is still a token, the issue cannot send — driving clicks there is the reason card 3 exists.
- [ ] **No token sits inside an `alt` attribute.** Grep specifically for `alt="{{` and confirm zero hits. A token in alt renders raw braces to every reader with images blocked.

---

### 5. Spam-word scan

- [ ] Scan run, hits reviewed in context, own-copy hits cleaned.

**Method:** Strip HTML tags, decode entities, then regex the visible text with word boundaries against: buy · cash · money · sale · promotion · free · discount · cheap · earn · income · profit · guarantee · act now · limited time · urgent · click here · order now · special offer · risk-free · no obligation · winner · congratulations · miracle · amazing · 100% · credit card. **Print surrounding context for every hit** — a bare count is useless, because context decides whether a hit matters.

Judge each hit: news language in a news context is fine; sales language in a sales context is not. Then fix on sight:

- [ ] No `MONEY` category label anywhere (use `MONETIZATION`, `REVENUE`, `ECONOMICS`).
- [ ] No two trigger words adjacent (e.g. "free cash flow").
- [ ] No trigger word repeated within a few lines.
- [ ] Own copy — thesis, utility segment, card 3, house blurb — is clean. Sourced story copy gets latitude; ours does not.

---

### 6. Preheader is clean

- [ ] The preheader div is exactly `<div style="display:none;max-height:0px;overflow:hidden;mso-hide:all;">` with no `font-size` and no `color`.

**Method:** Grep the HTML for `font-size:1px`, `font-size:0px`, `font-size:2px` and `color:transparent`, and read the preheader line itself. Any near-zero font size on a hidden element trips SpamAssassin's `__FONT_INVIS` — 2.499 points, and it arms six sibling rules worth 2.5-3.5 each. Colour-matching-the-background is a different, near-worthless rule; do not "fix" this by adding a colour.

- [ ] There is **exactly one** hidden element in the whole email.

**Method:** Grep for `display:none` and count. More than one feeds `__STY_INVIS`.

---

### 7. Dates are current and correct

- [ ] The masthead date is the intended send date, not the drafting date.
- [ ] Every date inside the copy is still true on the send date — nothing described as "Thursday" or "next week" has already happened.
- [ ] Any date the research file flagged as unverified has been confirmed by a human against the primary document, or the story has been re-led.

**Method:** List every date in the issue. For each, name the source that establishes it. Anything resting on a secondary source for a time-critical claim — especially the lead story — gets a human opening the primary document before send. If the lead's date has moved, the issue needs a new lead, not a patch.

---

### 8. Footer is compliant and honest

- [ ] Company name and full physical address present.
- [ ] Unsubscribe link present in the footer, and a second one in the top bar.
- [ ] The cold-receipt line states plainly that this is outreach based on industry research — not phrasing that implies the reader opted in.
- [ ] A preference or frequency option is offered before the unsubscribe.
- [ ] The Primary-tab ask is present.
- [ ] Any niche disclaimer is present (e.g. "Regulatory reporting, not legal advice").

**Method:** Read the footer block in the rendered HTML, line by line, against this list. The honesty of the cold-receipt line is deliberate — it suppresses spam complaints, which are the real risk on a cold send. Do not let anyone soften it.

---

### 9. Banned words absent

- [ ] Verified absent: game-changing · unlock · revolutionize · imagine if · supercharge.

**Method:** Case-insensitive grep of the HTML for each term, including inflections (`revolutioniz`, `unlocks`, `unlocking`). Report zero hits, not "I didn't see any."

- [ ] No hype vocabulary generally, and every paragraph is 1-3 sentences.

---

### 10. Every link resolves

- [ ] Every outbound URL in the HTML has been fetched and returns a real page.

**Method:** Extract every `href` from the HTML, dedupe, and fetch each one. Check specifically that:

- [ ] Each story headline and its `Read more →` point at the **same** URL.
- [ ] Card 3's link and the house blurb's link both resolve to the live offer destination.
- [ ] No `http://` where `https://` exists, and no tracking-stripped or truncated URLs.

A link that 404s on send day is worse than no link — it reads as a broken publication.

---

### 11. Mention budget and format spec

- [ ] Exactly two house mentions: card 3 and the bottom blurb. Not one, not three. Footer boilerplate does not count, and must not be used to smuggle in a third.
- [ ] Subject line: brand emoji + lead headline, under 55 characters.
- [ ] Preheader: `Plus: ...` naming two stories that are not the lead.
- [ ] Present and in order: masthead, banner, greeting, one thesis line, TOC bullets, divider, six cards with the house item at position 3, utility segment, house blurb, Keep Reading strip, named sign-off, footer.

**Method:** Read the rendered issue top to bottom against this list, then count the character length of the subject line literally.

---

### 12. Image payload weight

- [ ] The eight delivered JPEGs total roughly 140-215 KB.

**Method:** List the file sizes of `s0.jpg` through `s7.jpg` and sum them. Materially over the range means the resize or the quality setting did not take — re-export at 600px wide, JPEG quality 62. `.png` masters stay on disk and are not part of the payload.

- [ ] The `index.html` file itself is a sane size (the shipped issues run around 40 KB).

---

## Handoff

Only when all twelve pass:

- [ ] Zip the issue folder — `index.html` plus the eight `.jpg` files.
- [ ] Write the handoff note: what is in the package, what still needs a human decision, and what breaks if it is wrong.
- [ ] **Get explicit approval before anything sends.** This checklist clears a draft for handoff. It does not authorise a send.
