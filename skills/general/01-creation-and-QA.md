# General Skill — Creation Rules + Mandatory QA

**Run the §QA CHECKLIST before EVERY delivery and attach the filled report. If any BLOCKER fails, don't deliver — fix it first.** This encodes every mistake made so far.

> **⚠️ Updated Aug 5:** the "native card at position 3" and "exactly 2 offer mentions" BLOCKERS below apply ONLY to newsletters that use the news-card format + carry the offer (the flagships). **Niche/industry newsletters are now PURE EDUCATION — no native card, no CTA, no offer mentions.** Each newsletter's actual format lives in its own skill (`../newsletters/*.md`); see `newsletter-types.md`. Everything else here (sourcing, browser-verify, no fabrication, compliance, one-at-a-time) applies to all.

## Golden rules
1. **One newsletter at a time.** Never batch-produce. Deliver one, wait for review, then the next.
2. **Never fabricate** — no invented facts, stats, URLs, titles, dates, or frameworks. If you can't verify it on a live page, it doesn't go in.
3. **Verify every link in a REAL BROWSER, not curl/fetch.** Command-line fetchers get FALSE 404/403 from fda.gov, SHRM, pv-magazine, PR Daily and many publishers. Browser-load is the only source of truth. A curl 404 is not proof a link is dead; a "200" you didn't see load is not proof it's alive.
4. **Never deliver an unchanged file as "revised."** Diff against the prior version first.
5. **"Refresh" = replacing content** with new current sources — not re-sending the same stories.
6. **Never auto-send.** Draft only; Xander approves before any send, including tests.
7. **You never generate images** — you write prompts; Xander generates them.

## Sourcing & facts (BLOCKERS)
- Every story = a real, specific, CURRENT article + a concrete verifiable fact. Browser-confirm: (a) it loads, (b) it's the specific article (not a homepage/index/redirect), (c) the exact cited claim is on the live page — quote it in the QA report.
- Freshness: published within ~60 days. No stale stories under "Latest Developments."
- No duplicate story across cards. If you can't find enough real current stories, STOP and tell Xander.

## Native card (position 3) (BLOCKERS)
- Styled byte-identical to the news cards; headline a real `<a>` to the shared Medium article.
- Content MUST match the article — never invent a framework/step-list/stat. (Real "Power of Eight" = ~8 non-competing partner businesses; execution = Tracking / Terms / Follow-through. Do NOT invent an 8-step action list.)
- Fits the niche + the affiliate offer. $13.81B = US affiliate ad spend (attribute correctly).

## Compliance & brand (BLOCKERS)
- No "AI Integraterz" / "Published by AI Integraterz" anywhere. Footer = the newsletter's own name + physical address `37460 Beacon Brick Road, Zephyrhills, Florida 33541` + unsubscribe. No socials, no signup.
- NEVER "power partner" (→ "affiliate program"). Banned words (zero): game-changing, unlock, revolutionize, imagine if, supercharge.
- No false relationship claims on cold outbound (no "you signed up / expressed interest"). Neutral receiving line only.
- From = `<newsletter>@send.usingaitoscale.com`; Reply-To = `xander@usingaitoscale.com`; unique byline; CTA = `https://whimsy-nebula-47ch.here.now/`.
- Email-safe: 600px tables, inline styles, ASCII/HTML entities, one hidden preheader, merge tags `{{ MessageURL }}` / `{{ UnsubscribeURL }}` (no dot).
- TOC must match the actual cards (no dangling references).

## Deliverability & link reputation (BLOCKERS — added Aug 5 after the Local Affiliate Pro spam/flag incident)
- **Check every link's domain reputation BEFORE any send — not just that it loads.** One flagged link sends the whole email to spam.
  - Check each CTA / link domain at `transparencyreport.google.com/safe-browsing/search`. If it shows **"unsafe," DO NOT send** — it must be de-listed first (the domain owner requests a review in Google Search Console).
  - Run the campaign through **mail-tester.com** and read the report: SpamAssassin score, SPF/DKIM/DMARC, and especially **blocklist / Razor2 hits on the links** (a "Razor2 100%" hit = the content/links are already fingerprinted as spam).
- **No ephemeral / random-subdomain hosts as CTAs.** `*.here.now` preview URLs (e.g. `whimsy-nebula-47ch.here.now`, `aware-quarry-prs5.here.now`) and free-PaaS subdomains (e.g. the `*.up.railway.app` ListMonk host used for links/images/unsubscribe) read as phishing to spam filters. Use a stable, branded domain the business owns.
- Link/host reputation is a **domain-owner (Justin) fix, not a copy fix** — flag it and hold the send; never blast a list through a flagged link.

## Design + copy craft (BLOCKERS — Aug 6 lessons)
- **Apply a supplied design template FAITHFULLY.** When Xander gives a design direction (an HTML template), keep its style, layout, fonts, colors, formatting, spacing, and component types. Pour our content into ITS components. **Strip 100% of the template's original brand** (name, logos, people, addresses, images, copy). **Remove** template parts we can't fill; you may **add** only something simple + relevant that fits an existing slot. **Do NOT invent design elements** — no left-border quote bars, no colored callout boxes, no dark panels, no dividers that aren't in the original. Invented decoration = AI slop. If it isn't in the template, don't add it.
- **Greeting = "Hi {first name}," with a merge tag + fallback** (never "good morning," never a blank "Hi ,"). ListMonk: `{{ if .Subscriber.FirstName }}{{ .Subscriber.FirstName }}{{ else }}there{{ end }}`. Sendy: `[FirstName,fallback=there]`. Confirm the list carries first-name data. (Headline-led news titles with no greeting line can skip it.)
- **Emphasis, restrained.** Bold the few highest-value phrases (key stats, the one-line thesis) so a skimmer catches them, plus the design's accent color on ~1 phrase per issue. 3–4 emphases per issue, max — not a highlighter dump.
- **Images:** editorial craft, never literal-metaphor AI slop; never blank paper (see `05-images.md`).

## THE QA CHECKLIST — fill PASS/FAIL + evidence; attach as the QA report
**A. Sourcing (BLOCKER):** every link browser-loads (list URL+status) · each is the specific article · each cited claim is on the page (quote it) · every story ≤~60 days (list dates) · no duplicate stories.
**B. Native card (BLOCKER):** real `<a>` to the Medium article · framework/claims match the article (nothing invented) · themed to niche + offer · $13.81B attributed correctly.
**C. Compliance (BLOCKER):** no AII / "Published by AI Integraterz" · no "power partner" · zero banned words · no false relationship claim · footer has address + unsubscribe, no socials/signup · From/Reply-To/byline/CTA correct.
**D. Format (BLOCKER):** TOC matches cards · exactly 2 offer mentions · email-safe HTML (600px, inline, ASCII, one preheader, correct merge tags).
**E. Design:** built on the locked Front Desk template; not redesigned.
**F. Hygiene:** file differs from prior version · image prompts included · QA report attached · no auto-send.
**G. Deliverability / link reputation (BLOCKER):** every CTA/link domain checked on Google Safe Browsing (not flagged) · campaign run through mail-tester (score + SPF/DKIM/DMARC + no Razor2/blocklist hit on links) · no ephemeral `*.here.now` / free-subdomain CTA.
**H. Design + craft (BLOCKER on redesigns):** supplied design applied faithfully (source brand 100% stripped; no invented elements/slop) · greeting = `Hi {first name}` + fallback (not "good morning") · emphasis restrained (key phrases bold + &le;1 accent-color phrase).

Deliver ONLY when every BLOCKER passes.
