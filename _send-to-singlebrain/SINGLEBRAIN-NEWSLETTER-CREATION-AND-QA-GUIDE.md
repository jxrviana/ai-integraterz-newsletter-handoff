# SingleBrain — Newsletter Creation + Mandatory QA Guide

**Xander: paste this to SingleBrain and tell it to SAVE this as a skill/document and follow it on every newsletter from now on.**

---

**SingleBrain: adopt this as a permanent skill. From now on you create outbound niche newsletters end-to-end AND run the full QA checklist in §10 BEFORE delivering anything to Xander. Attach the completed QA report to every delivery. If any BLOCKER check fails, do NOT deliver — fix it first.** This guide encodes every mistake made so far and how to avoid it.

## 0. GOLDEN RULES (never break these)
1. **One newsletter at a time.** Never batch-produce multiple. Deliver one, wait for review, then the next. (Batching is what caused slop before.)
2. **Never fabricate anything** — no invented facts, stats, URLs, article titles, dates, or frameworks. If you cannot verify it on a live page, it does not go in.
3. **Verify every link in a REAL BROWSER, not curl/fetch.** Command-line fetchers get FALSE 404/403 from fda.gov, SHRM, pv-magazine, PR Daily and many publishers. Browser-load is the only source of truth. A curl 404 is NOT proof a link is dead; a "200" you did not see load is NOT proof it is alive.
4. **Never deliver an unchanged file as "revised."** Diff against the previous version first; if nothing changed, don't deliver it. (You recently re-sent 5 byte-identical files as revisions — never again.)
5. **"Refresh" means replacing content** with new, current sources — not re-sending the same stories.
6. **Never auto-send.** Draft only. Xander reviews and approves before any send, including tests.
7. **Run the §10 QA checklist before EVERY delivery and attach the filled report.** No newsletter ships without a passed QA report.
8. **You never generate images** — you write image prompts; Xander generates them.

## 1. WHAT THESE NEWSLETTERS ARE
Outbound cold emails formatted as genuine editorial trade newsletters. The reader must experience a real publication — straight news + genuine value. The affiliate-program offer appears as exactly TWO touches: (1) ONE native "story" card at position 3, styled byte-identical to the news cards, and (2) one short house blurb near the bottom. Nothing else sells.
- Each newsletter has its own brand name, tagline, unique byline, niche.
- The offer is always **"the affiliate program."** NEVER "power partner."

## 2. SOURCING & FACTS — the #1 place things go wrong (all BLOCKERS)
- Every news story = a real, specific, CURRENT article + a concrete, verifiable fact/number from it.
- For EVERY external link, in a real browser confirm all three: (a) it loads (200 in a browser); (b) it goes to the SPECIFIC article — not a homepage, blog index, search page, or Google-News redirect; (c) the exact stat/claim the newsletter attributes to it actually appears on that live page. Quote the supporting sentence in the QA report.
- FRESHNESS: stories must be published within ~60 days of the send date. No stale stories under "Latest Developments." (The Green Room shipped 17–20-month-old stories — never again.)
- NO DUPLICATE STORY across cards (don't cover the same event twice).
- If you cannot find enough real, current stories for a niche, STOP and tell Xander. Do not pad with stale or invented material.

## 3. THE NATIVE CARD (position 3) — all BLOCKERS
- Styled byte-identical to the news cards (same label/headline/image/bullets structure).
- Headline is a real clickable link (an `<a>`, NEVER a plain `<span>`), pointing to the shared Medium affiliate article.
- Its content MUST MATCH the linked article. NEVER invent a framework, a step-list, or stats.
  - The real **"Power of Eight"** = partnering with ~8 non-competing businesses that serve the same customer, committed to promoting each other. Execution = **Tracking / Terms / Follow-through.** Do NOT invent an 8-step action list. (The People Person fabricated "Trigger/Ask/Submit/Acknowledge/Review/Decide/Notify/Reward" — that appears nowhere in the article. Never do this.)
- The card must fit the newsletter's niche AND the affiliate offer — not a recruiting pitch dropped into a solar newsletter (The Daily Sun did that — wrong).
- The only external stat allowed here, **$13.81B**, is **US affiliate ad spend** (eMarketer 2025 forecast for 2026, up 11.3% from $12.42B). Attribute it correctly; don't misapply it to the niche's own spend.

## 4. FORMAT & STRUCTURE
Each issue: masthead (brand + tagline + issue no. + date) → byline → intro (1 POV thesis line) → "In this issue" TOC → divider → 4–6 story cards → a utility/"playbook" segment that teaches something free → house blurb + CTA → sign-off → footer.
Each story card: small all-caps category label → emoji + headline (linked) → image → "Image source:" caption → "The Short Version" → "The Details" (4 UNIQUE bullets) → "Why It Matters" → "Read more →".
- **The TOC must match the actual cards.** If you change a card, update the TOC and intro. (The Protocol's TOC still promised a "TRAVERSE clinical-practice" story after that card was swapped — dangling reference; never leave these.)

## 5. COMPLIANCE & BRAND (all BLOCKERS)
- **No "AI Integraterz" anywhere. No "Published by AI Integraterz."** All AII branding is stripped. Footer = the newsletter's OWN name + the physical address `37460 Beacon Brick Road, Zephyrhills, Florida 33541` + an unsubscribe link. NO social links. NO signup link.
- **NEVER "power partner."** Always "affiliate program."
- **Banned words (zero occurrences):** game-changing, unlock, revolutionize, imagine if, supercharge.
- **No false relationship claims.** This is cold outbound — never write "you signed up," "you expressed interest," etc. Use a neutral receiving line (e.g., "You're receiving this as a [niche] professional."). (The Green Room's "you expressed interest in PR agency industry analysis" is banned.)
- From = `<newsletter>@send.usingaitoscale.com`; Reply-To = `xander@usingaitoscale.com`; unique byline per newsletter.
- CTA link = `https://whimsy-nebula-47ch.here.now/` (current standard for all newsletters).
- **Email-safe HTML:** 600px table layout, all inline styles, HTML entities (ASCII-only — no smart quotes / em-dashes), exactly ONE hidden preheader div, images with graceful fallback. Merge tags `{{ MessageURL }}` / `{{ UnsubscribeURL }}` (NO dot).

## 6. DESIGN
Use the saved **Front Desk (Rundown) locked template** as the literal base — fill content into its slots. Do NOT redesign, restyle, or invent a new look. Design fidelity to that template is required.

## 7. IMAGES
Write labeled, text-free Higgsfield prompts (one per slot: banner, s1, s2…). Photorealistic editorial; a different look per slot; NO writable object in the scene (no paper/screens/signs). Xander generates the images. You never generate images.

## 8. LISTMONK TECHNICAL
Blank/raw template (ID 8) so the body isn't double-wrapped. Host images via the media API. Confirm `individual_tracking: true`, open + click tracking on, bounce processing on (hard→blocklist). To verify open/click tracking, use a **real campaign send to a seed list — not the test button** (test emails don't reliably wrap tracked links).

## 9. PROCESS & DELIVERY
- One newsletter at a time; diff against the prior version; never ship unchanged as "revised."
- Deliver as: the `.html` file + the image prompts + the completed QA report. Never paste the newsletter as chat text; attach the file.
- Never auto-send. Xander approves the ListMonk preview before any send.

## 10. THE QA CHECKLIST — run before EVERY delivery; attach the filled report
For each item: PASS/FAIL + evidence. Every BLOCKER must PASS or you do not deliver.

**A. Sourcing (BLOCKER)**
- Every external link browser-loads (200) — list each URL + status.
- Each link goes to the specific article (not homepage/index/redirect).
- Each cited stat/claim appears on the live page — quote the sentence.
- Every story published within ~60 days — list each story's date.
- No duplicate story across cards.

**B. Native card (BLOCKER)**
- Position-3 card headline is a real `<a>` linking to the shared Medium article.
- Its framework/claims match the article — nothing invented.
- Themed to this niche + the affiliate offer.
- $13.81B attributed correctly (US affiliate ad spend).

**C. Compliance/brand (BLOCKER)**
- No "AI Integraterz" / "Published by AI Integraterz" anywhere.
- No "power partner."
- Zero banned words.
- No false relationship claim in footer/intro.
- Footer has the physical address + unsubscribe; no social/signup links.
- From/Reply-To/byline correct; CTA = the standard URL.

**D. Format (BLOCKER)**
- TOC matches the actual cards (no dangling references).
- Exactly 2 offer mentions (native card + bottom blurb).
- Email-safe HTML: 600px, inline styles, ASCII entities, one preheader, correct merge tags.

**E. Design**
- Built on the locked Front Desk template; not redesigned.

**F. Delivery hygiene**
- File differs from the prior version (not an unchanged re-send).
- Image prompts included. QA report attached. No auto-send.

**Deliver the newsletter ONLY when every BLOCKER passes, with this filled checklist as the QA report.**
