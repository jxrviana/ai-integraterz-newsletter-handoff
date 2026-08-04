# SKILL â€” Outbound Newsletter Production

*A complete, portable build procedure. Give this to any capable agent along with a niche and an offer, and it produces an issue to standard without any other context.*

*Companion spec: `NEWSLETTER-PLAYBOOK.md` - its CRITICAL-UPDATES rules 1-22 OVERRIDE this doc wherever they conflict. Worked example of a complete built issue: `ready-to-send/the-protocol/`. Research example: `research/RESEARCH-MENS-HEALTH-NEWSLETTER.md`. Deliverability (separate job): `deliverability/DELIVERABILITY-RUNBOOK.md`.*

> **Current overrides (2026-07-30), on top of playbook rules 13-22:**
> - Finished issues are assembled as a **self-contained folder in `ready-to-send/<newsletter>/`**: `index.html` + `images/` + `medium-article.html/.md` + source `*-ISSUE-1.md` + `research/` + a SingleBrain `*.zip` (zip excludes `images/masters/`). Move the folder to `1-SENT/` once emailed; superseded versions go to `MISCELLANEOUS/`.
> - **Byline = Jay Bell** on every newsletter; the masthead brand mark is a small logo image, never an emoji character.
> - **Card 3** "Read more" -> the Medium article; the offer-page CTA (`/blueprint` etc., per `offers/CTA-LINKS-BY-NICHE.md`) sits ONLY on the bottom house blurb. **Reply-To = `xander@usingaitoscale.com`** on every campaign.
> - Build via a **multi-agent Opus pipeline**: research (parallel) then copy then HTML + Medium + images (in parallel).

---

## 1. What this skill produces

An **outbound newsletter**: a cold email formatted as a genuine trade publication for one business niche. The reader experiences a real trade brief â€” six news stories, verified numbers, a category label and an image on every block â€” and the sender's own offer appears as **ONE story block at position 3, styled identically to the news around it**, plus one short blurb near the bottom. It is not a sales email in a costume; it is a real publication that carries the sender's announcement in an editorial slot. Every issue ships as three artifacts: **(a)** a markdown content file `<NAME>-ISSUE-<N>.md` holding the copy, staging notes, placeholder map, image briefs and a source table; **(b)** an email-safe HTML file `<name>-issue-<n>/index.html`; **(c)** **eight images** in `<name>-issue-<n>/images/` â€” `s0` banner, `s1`â€“`s6` story images, `s7` utility segment â€” delivered as 600px JPEGs with the .png masters kept alongside.

---

## 2. When to use it / when not to

| Use it for | Do not use it for |
|---|---|
| Cold outbound to a named business niche where the reader has not opted in | Opt-in newsletters to an owned list â€” those need a different footer, a different greeting, and no "you came up in our research" line |
| A publication the sender intends to run repeatedly (issue #1 is built so issue #2 is cheap) | One-to-one outreach or personalised prospecting emails â€” this format is mass-produced by design |
| An audience of **owners and operators**, addressed as operators | Consumers or patients â€” the whole register assumes a business reader |
| A situation where the offer can honestly be written up as an announcement | A straight sales email, a promo blast, a launch announcement, or anything where the ask is the point |

---

## 3. Inputs you need before starting

Do not start Stage 1 until every row is filled. Missing items are the single biggest cause of a rebuild.

| Input | Why it matters | Example |
|---|---|---|
| **Niche + precise audience** | Decides pillars, vocabulary, register. Name *which businesses*, not which market. | "Owners and operators â€” men's health clinics/medical directors, peptide/telehealth brands, coaches." Not "men's health." |
| **The offer** | Becomes card 3. Must be a real capability, result or asset. | "A partner network connecting clinics to referral partners, niche creators and podcasts." |
| **Destination URL for card 3** | Card 3 exists to drive clicks. No URL, no reason to build it. | A published article acting as the third-party "source" for the announcement. |
| **Second destination for the house blurb** | The blurb's CTA. A case study works better than repeating card 3's link. | `aiintegraterz.com/case-studies/mens-health.pdf` |
| **Company name** | Footer identification; also card 3 and the blurb when the sender is the advertiser. | AI Integraterz |
| **Physical mailing address** | Legally required in the footer (CAN-SPAM). No address, no send. | 37460 Beacon Brick Road, Zephyrhills, Florida 33541 |
| **Sending domain** | Determines link domains and the deliverability work. | scaleverticalwithai.com |
| **Cold or opted-in** | **Changes the footer wording.** Cold gets the honest line. Never claim a subscription that did not happen. | "You're reading this because your business came up in our research on the men's health industry." |
| **Whose offer it is** | When advertising for a client, the client is the advertiser in card 3 and the blurb; the sender appears **only** in the footer legal line. | *The Green Room* advertises SpeakerAgent AI; AI Integraterz is footer-only. |
| **Publication identity** | Name, fixed brand emoji (same every issue), tagline, issue number, send date, sign-off name. | ðŸ§¬ THE PROTOCOL â€” "The business of helping men live their 50s like their 20s." |

---

## 4. The five stages

### Stage 1 â€” Research

**Do this.** Define 5â€“6 coverage pillars for the niche before searching (regulatory weather Â· market and business moves Â· clinical or product developments Â· acquisition and retention Â· technology and AI Â· case story). Find **10â€“12 candidate stories** spread across those pillars. Fetch every source and confirm it actually loads. Record for each candidate: category, source name, URL, corroborating URL, date, a plain "what happened" paragraph, 4â€“6 detail bullets with the raw numbers, a "why it matters" paragraph, and the pillar it fills. Close the file with a **Recommended five**, a nominated lead story with the reason, strong alternates, a pillar-coverage note naming the weakest pillar, a list of items sourced to secondary aggregators, and a list of sources rejected as unusable.

**Source hierarchy.** Primary documents and peer-reviewed papers first. Trade press and authoritative industry reporting second. Law-firm and professional-services analyses are acceptable as **flagged secondary** when the primary is blocked â€” and only when two independent analyses agree. Reject content farms and vendor marketing outright: on the men's health pass, a site claiming "2048% IRR" was excluded as implausible, a patient-acquisition-cost benchmark was excluded because it disclosed n=4 for endocrinology, and a "34% rejection rate spike" figure circulating in agency blogs was excluded because it was self-described as an estimate with no attribution to the platform.

**Done looks like.** A `RESEARCH-<NICHE>-NEWSLETTER.md` file, opening with a verification note that states the date every URL was fetched and confirmed loading, and naming which outlets were paywalled or blocked and what replaced them.

**Hard rule.** *If a number cannot be traced to a page you actually fetched, it does not ship.* Not "it looked right," not "the search snippet said so."

**Failure modes.** Taking a search-result snippet as a source. Using a vendor's own statistic to prove the vendor's category is growing. Silently promoting a secondary source to primary. Filling all five slots from one pillar. Leaving a date discrepancy unrecorded â€” flag it in the file and hedge the copy ("in early March") rather than picking a date.

### Stage 2 â€” Draft

Write `<NAME>-ISSUE-<N>.md` against this skeleton, in this order:

```
SUBJECT     [fixed brand emoji] + lead story headline        under 55 characters
PREHEADER   "Plus: [story 2], [story 4]."
MASTHEAD    Emoji + NAME Â· tagline Â· Issue # Â· lead headline Â· byline + date Â· Read Online | Unsubscribe
BANNER      s0 (branded, not a story image)
GREETING    "Good morning, [audience noun]."               e.g. "Good morning, operators."
THESIS      ONE sentence of POV framing the whole issue
TOC         4 bullets + a "Plus:" bullet
DIVIDER     LATEST DEVELOPMENTS
STORY 1-6   six cards; CARD 3 IS THE HOUSE ANNOUNCEMENT
UTILITY     a teaching segment that gives something away free, image s7
HOUSE       2-3 line blurb + one CTA link         <- second and final mention
KEEP READING  3 teasers with "Plus:" sublines
SIGN-OFF    a named human + a one-line promise
FOOTER      company Â· address Â· honest cold line Â· unsubscribe Â· preference downgrade Â· Primary-tab ask
```

**The story formula**, identical on all six cards:

1. Small all-caps category label (`FDA`, `DEA`, `MARKET`, `RETENTION`, `CASE STUDY`).
2. Emoji + headline, **the headline itself hyperlinked** to the source.
3. Image.
4. **The Short Version:** one paragraph, 40â€“70 words, what happened, plainly. **The Details:** 4 bullets carrying the specifics and the numbers. **Why It Matters:** one paragraph of analysis â€” what this changes for the reader. *(If the research only supports a single summary paragraph, use `TL;DR:` throughout the issue instead â€” see the standing lesson in Â§5.)* **Never use "The Rundown:" as a label â€” that is another publication's masthead.**
5. `Read more â†’` pointing at the same URL as the headline.

**Card 3 â€” the native announcement.** The offer goes in the middle of the run, never last: last is the ad position, middle is the editorial position. It carries a real category label (`PARTNER NETWORK`, `PODCAST TECH`), the same emoji weight, image slot, skeleton and `Read more â†’`. No "sponsored" label, no tonal shift, no second person, no adjectives of excitement â€” it reads as flatly as the regulatory story above it. **Why:** a reader scanning the issue processes it as the third news item of the day and clicks it for the same reason they click the others. The moment it announces itself as an ad it is skipped, and the entire issue was built to deliver that one click. It does not have to be news â€” any real capability, result or asset can be written up as an announcement.

**Copy rules.**

- Numbers carry the weight; specificity *is* the credibility: "33,607 commercially insured adults," "$751 million in cash."
- One idea per paragraph, 1â€“3 sentences. Mobile-first. Address the reader as an operator, never as a subscriber or a friend.
- **Banned outright:** game-changing Â· unlock Â· revolutionize Â· imagine if Â· supercharge.
- **Mention budget: exactly 2** â€” card 3 and the house blurb. One is a wasted send; three is an ad. The footer company line is boilerplate, not a mention.
- **Spam-word discipline.** Minimise, do not ban: buy Â· cash Â· money Â· sale Â· promotion Â· free Â· discount Â· cheap Â· earn Â· income Â· profit Â· guarantee Â· act now Â· limited time Â· urgent Â· click here Â· order now Â· special offer Â· risk-free Â· winner Â· amazing Â· 100%. Density and register decide it â€” "Cash and short-term investments $751 million" is financial reporting. **Fix on sight:** never a `MONEY` category label (use `MONETIZATION`, `REVENUE`, `ECONOMICS`); never two trigger words adjacent; never the same one twice in a few lines. Copy we write ourselves must be clean; sourced story copy gets latitude, because rewriting it risks accuracy.

**Done looks like.** The markdown file also carries subject-line options with character counts, a placeholder table, an image-slot table with one direction per slot, a links section, pre-send checks, and a **Sources used** table with the caveat carried forward for every story.

**Failure modes.** Writing the house block as a teaching essay instead of an announcement. Making only `Read more â†’` clickable â€” that halves the click surface. Inventing "The details" bullets the source does not support in order to fill the format.

### Stage 3 â€” Images

**Do this.** Photorealistic editorial or press photography only â€” never illustration, vector, 3D render or infographic. **Use a different model per slot**; no model more than twice in an issue. That is the single biggest variety lever. Vary lighting, colour temperature, composition, focal length and mood on every slot, and art-direct each slot independently â€” never write a reusable style block. Put the test in the brief: **if any two images look like the same shoot, it failed.** Read all eight directions side by side before generating and confirm no two share a subject.

**No text in any image** â€” and a "no text" clause is not sufficient. The real rule: **choose concepts where no surface in frame could plausibly carry lettering.** High risk: whiteboards, screens, notebooks, product packaging, book spines, vehicle grilles or livery, equipment badges, building facades. Safe: bare ground, sky, asphalt, fabric, foliage, coiled cable, empty rooms, unbranded tools, water, food, hands. The strongest images across five sets were the emptiest â€” an attic, a hearing room, "a row of unlabeled amber-capped vials on a grey government conference table."

**No identifiable people.** No faces, no stock-photo doctors, no before/after imagery.

**The exception that matters.** The house-announcement image (`s3`) must **not** be the visual outlier. It sits among the news images at the same width and aspect ratio. Any visual signal that it is a promo defeats the mechanic.

**Delivery specs.** 600px wide, JPEG quality 62, roughly 140â€“215 KB total for all eight. Keep the .png masters. Declare `width="600"` on the banner and `width="594"` on story images â€” **never larger than the source**, or the client upscales it and it looks cheap.

**Done looks like.** Eight files, inspected. **Look at them with a Read call â€” never trust an agent's self-report.** Inspect the master at full size, zoom any text-capable surface, then check the 600px delivery file; defects invisible at delivery size do not matter.

**Failure modes.** Locked style block across all eight (this got the first two sets rejected as "templated, cheap, AI slop"). A generator silently defaulting to low quality or a low resolution tier â€” force quality and size explicitly. Two slots with the same subject. Patching a surviving label by cloning texture and not disclosing it â€” that is a hand edit and must be declared.

### Stage 4 â€” HTML build

Build `index.html` from the markdown. Email clients are not browsers.

| Requirement | Detail |
|---|---|
| Layout | Nested `<table role="presentation">` only. No divs for structure, no flex, no grid. |
| Styles | **Every style inline.** No external CSS, no `<style>` blocks beyond a single link-colour rule, no JavaScript, no web fonts. |
| Fonts | System stack: `-apple-system,'Segoe UI',Roboto,Helvetica,Arial,sans-serif` â€” repeated on every element that renders text. |
| Column | 640px max-width, centred, on a `#f4f4f5` page background; cards `#ffffff` with a `1px solid #e5e7eb` border and `6px` radius. |
| Outlook | MSO ghost table wrapping the column: `<!--[if mso]><table role="presentation" width="640" ...><tr><td><![endif]-->` â€¦ closed at the end. Plus the `PixelsPerInch` OfficeDocumentSettings block in `<head>`. |
| Preheader | Exactly `<div style="display:none;max-height:0px;overflow:hidden;mso-hide:all;">` â€” **nothing else.** No `font-size`, no `color`. |
| Hidden elements | **Exactly one** in the whole email (the preheader). Repeated `display:none` compounds risk. |
| Images | `width="594"` story / `width="600"` banner, plus `style="width:100%; max-width:594px; height:auto; display:block; border:0;"` and a placeholder background colour so blocked images still show a shape. |
| Alt text | **Real literal alt text** â€” the headline, spelled out. **Never a merge token inside an `alt` attribute.** |
| Links | Headline and `Read more â†’` both linked, both to the same URL. Every `<a>` carries its own inline font, size, colour and `text-decoration`. |
| Entities | Encode em dashes, quotes and emoji as HTML entities (`&mdash;`, `&rsquo;`, `&#129514;`) so nothing mangles in transit. |

**Failure modes.** Any near-zero `font-size` on the preheader (see Â§6). Declaring an image wider than the source. A merge token in an `alt`. Assuming the ESP will fix your markup â€” it will not.

### Stage 5 â€” QA

Run every check. Each one has a method; "I looked at it" is not a method.

| Check | How to verify |
|---|---|
| Every statistic traces to a fetched source | Walk the Sources table row by row against the research file. Any number without a row does not ship. |
| Card 3 is style-identical to the news cards | **Programmatically.** Extract the tag skeleton and every `style` attribute from all six cards and diff them. Cards 2â€“6 must be byte-identical to card 1. The eye will not catch a 2px padding difference â€” and that difference is what tells a reader "this one is an ad." |
| Every image resolves | Enumerate `src` values, confirm each file exists at the stated path, and confirm the declared width is not larger than the file's real width. |
| No leftover placeholders | Grep for `{{` and `TODO` and `PLACEHOLDER`. The only survivors allowed are the ESP's own merge tags for unsubscribe and view-online, and those must be listed in the staging notes. |
| Spam-word scan | Strip tags, decode entities, regex the Â§2 list with word boundaries against visible text, and **print surrounding context** â€” a bare count is useless. |
| Preheader clean | Confirm the div carries only those four declarations, and that it is the only hidden element in the file. |
| Dates current | Confirm the masthead date, the send date and every date claim inside the copy. A dated lead that has already happened destroys the issue's premise. |
| Footer complete | Physical address present, unsubscribe present in **both** the masthead and the footer, preference downgrade offered, Primary-tab ask present, cold-send line honest. |
| Banned words absent | Grep the five. |
| Mention count | Exactly 2 editorial mentions. |
| Render check | Open the HTML and look at it. Confirm the images load and card 3 does not stand out. |

---

## 5. The quality rules that override everything

1. **No fabricated facts, ever.** Every statistic traces to a real page that was fetched. This is the whole product.
2. **Vendor research is labelled as vendor research.** If a number comes from a company selling into the category, say so in the source table, or cut it.
3. **A format upgrade never justifies unsourced copy.** *The People Person* was rebuilt toward the three-part skeleton; converting its stories would have meant inventing "The details" bullets and "Why it matters" analysis no source supported, so it correctly kept `TL;DR:` throughout. If a niche needs the richer skeleton, that is a research pass, not a rewrite pass.
4. **Honest cold-send footer.** Say plainly that the reader's business came up in research. Never imply a subscription that did not happen â€” the honesty suppresses spam complaints, the real risk on a cold send.
5. **Nothing sends without explicit human approval** in the current conversation. Draft, test-send, and stop.
6. **Format parity on card 3 is not negotiable.** Any edit that makes it read like a promo undoes the entire issue.

---

## 6. Common failure modes and how they were caught

| What happened | How it was caught | The rule it produced |
|---|---|---|
| House content sat at **position 6 (last)** â€” the ad slot â€” and was a teaching essay with **no hyperlink of any kind**, so it drove zero clicks | Format audit of the draft against the native-announcement directive | House block goes to **position 3** with a real category label; headline **and** `Read more â†’` both linked to the same destination |
| Only `Read more â†’` was clickable on story cards | Same audit | Every story headline is a link â€” otherwise you halve the click surface |
| Spam score stuck at 3.6. The working theory was colour-matched-background text. That theory was **wrong** â€” the real trigger was `font-size:1px` on the preheader | Read the actual SpamAssassin rule source, then re-ran mail-tester after removing it: **3.6 â†’ 10/10** | Preheader carries `display:none;max-height:0px;overflow:hidden;mso-hide:all;` and nothing else. A near-zero font size fires `__FONT_INVIS` (2.499 points) and arms six sibling rules worth 2.5â€“3.5 each. Colour-matching is a different, near-worthless rule â€” do not confuse them |
| **Two image slots briefed with the same subject** â€” twice: two van scenes in the HVAC set, two empty-studio-with-chairs in the podcast set. Cost two re-shoots | Reading the eight directions together, after generation | Read all eight briefs side by side **before** generating |
| First two image sets rejected by the client as "templated, cheap, AI slop" | Client review | Photorealistic only, a different model per slot, art-direct each slot independently, force quality/resolution explicitly â€” one generator silently defaults to low quality |
| A **merge token inside an `alt` attribute** â€” renders as raw `{{...}}` text whenever images are blocked, which is most first opens | Grepping `alt="` for `{{` | Alt text is always literal. Merge tokens live in `href` and body copy only |
| **Emoji converted to shortcodes in transit**, so the subject arrived as text instead of the brand marker | ESP test send, read in a real inbox | Encode emoji as HTML entities or real Unicode and confirm in a live test send â€” never assume the ESP preserved them |
| **Markdown pasted into a platform that does not parse markdown**, so asterisks and brackets shipped as literal characters | Test render in the platform | The markdown file is for humans; **only the built HTML goes into an ESP**, and only in raw-HTML mode |

---

## 7. Handoff to the ESP

Give the sending agent: the built `index.html`, the eight 600px JPEGs, and the staging notes (placeholder map, links list, pre-send checks). Then it must:

1. **Upload the eight images to the ESP's own image library.** Never host them on someone's personal hosting, and never deploy anything anywhere without explicit permission â€” ESPs host their own images, and that is the correct path.
2. **Swap the image paths** from `images/sN.jpg` to the ESP-hosted URLs; confirm each loads in a browser.
3. **Insert the platform's real unsubscribe and view-online merge tags** in place of `{{UNSUBSCRIBE_LINK}}` and `{{VIEW_ONLINE_LINK}}` â€” in both the masthead and the footer.
4. **Paste into raw-HTML mode. Never a drag-and-drop builder** â€” visual builders rewrite tables, strip inline styles and break the MSO ghost table.
5. **Save as a draft.** Do not schedule, do not send to a list.
6. **Test-send to a seed address** and check it in a real inbox: images load, emoji render, card 3 does not stand out, links resolve to real tracked URLs with per-recipient IDs.
7. **Verify in raw headers**, not in the vendor's dashboard: SPF pass, DKIM pass, alignment, and both `List-Unsubscribe` and `List-Unsubscribe-Post` present. Vendor docs have made a compliant feature look missing; a cached resolver has made a live DNS record look absent. Read the headers.
8. **Report back and stop.** The send decision belongs to a human.

Deliverability setup itself â€” SPF, DKIM, DMARC, warming, placement testing â€” is a separate procedure. See `DELIVERABILITY-RUNBOOK.md`.

---

## 8. The reusable agent briefs

The `templates/` folder holds the ready-made prompt for each stage, so this skill can be executed by five separate agents without re-deriving the instructions:

| File | Stage | Must specify |
|---|---|---|
| `templates/01-research-brief.md` | 1 | Niche, audience, pillars, candidate count, source hierarchy, the fetch-and-confirm rule, the output file shape |
| `templates/02-draft-brief.md` | 2 | The full skeleton, the story formula, the card-3 rule, mention budget, banned and spam words, the required staging-notes tables |
| `templates/03-image-brief.md` | 3 | Eight slot directions written out individually, the different-model-per-slot rule, the no-lettering-possible rule, the s3 exception, delivery specs |
| `templates/04-html-build-brief.md` | 4 | Every row of the Stage 4 table, plus the markdown file as input |
| `templates/05-qa-checklist.md` | 5 | The Stage 5 table with the verification method for each row, and instruction to report failures rather than silently fix them |

Fill the Stage 3 inputs into the brief before dispatching. An agent given a brief with an unresolved input will invent one.

---

*This is a living document. Newsletter quality on this project is explicitly not locked in â€” when the standard improves, update this file and the playbook together.*
