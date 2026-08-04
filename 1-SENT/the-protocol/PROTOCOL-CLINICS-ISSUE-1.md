# THE PROTOCOL — Issue #1 (Clinics Edition) — COPY SOURCE OF TRUTH

**Status:** DRAFT for HTML build. Nothing sent. Nothing approved.
**Written:** July 30, 2026
**Audience:** Owners/operators of men's-health clinics, hormone/TRT clinics, peptide & supplement brands, telehealth/GLP-1 providers, and med spas. This is business & regulatory intelligence for people who RUN these businesses — not medical advice.
**Every fact traces to the research files** (`research-protocol/stories-verified.md`, `research-protocol/stories-fresh.md`, `RESEARCH-MENS-HEALTH-NEWSLETTER.md`). See the Fact-Trace appendix at the bottom.

---

## BUILD NOTES FOR THE HTML AGENT (read first — not part of the email)

- **NO LITERAL EMOJIS ANYWHERE** in the rendered email (subject, masthead, headlines, category labels). Per Playbook Critical Update #1: emojis are an AI tell and mojibake to `???` in some clients (already happened on the prior `PROTOCOL-ISSUE-1.md`). The Protocol's brand mark is a **DNA double-helix emblem rendered as a real logo graphic** (the "🧬" identity, drawn — never the emoji character) beside the wordmark, per Critical Update #8.
- **SIX story cards.** Card 3 is the house announcement and MUST be byte-identical in structure/style to cards 1, 2, 4, 5, 6 (same template, label treatment, image size, "Read more →"). Verify by diffing style attributes across all six cards (Playbook §6). Do not let it read as an ad.
- **Card labels:** use the canonical set — `The Short Version:` / `The Details:` (four bullets) / `Why It Matters:`. Do NOT use "The Rundown:" (Playbook §5).
- **Mention budget = exactly 2 house mentions:** Card 3 + the House Blurb. Nothing else. The footer publisher line is legal identification, not a promotional mention.
- **Design:** build from `design-directions/v2/`; recommend `html-3` (Bold v2, locked primary) recolored to The Protocol's palette. Final design call is yours.
- **Images: 8 total** — banner (s0), one per card (s1–s6), one for the utility segment (s7). One-line slot briefs are inline below; full production per Playbook §8 (photorealistic editorial, a different model + lighting per slot, text-safe subjects, no two from the "same shoot," and **s3/house image must NOT be the visual outlier**). Declare `width="600"` on banner, `width="594"` on story/utility images.
- **Placeholders to leave literal:** `https://medium.com/@ai_integraterz/the-paid-acquisition-playbook-is-closing-for-mens-health-clinics-here-is-the-one-that-isn-t-07172d95e2bb` (Card 3 Read more), `{{VIEW_ONLINE_LINK}}`, `{{UNSUBSCRIBE_LINK}}`.
- **Preheader div** exactly: `<div style="display:none;max-height:0px;overflow:hidden;mso-hide:all;">` — no font-size, no color:transparent (Playbook §7). One hidden element only.
- **Encoding:** `<meta charset="utf-8">`; use HTML entities (`&mdash;` `&rsquo;` `&rarr;`) for punctuation.
- Banned words checked (game-changing, unlock, revolutionize, imagine if, supercharge): none used. Spam-word register kept clean in house-written copy.

---

## ===== SUBJECT LINE =====

**The FTC just sued Hims &amp; Hers**

*(29 characters, text-only, no emoji.)*

## ===== PREHEADER =====

**Plus: the peptide panel's verdict, and the prescribing clock that runs out Dec 31.**

---

## ===== MASTHEAD =====

- **Brand mark:** DNA double-helix emblem (logo graphic, not the emoji character)
- **Wordmark:** THE PROTOCOL
- **Tagline:** The business of helping men live their 50s like their 20s.
- **Issue label:** Issue #1 · Clinics Edition · Wednesday, July 30, 2026
- **Lead headline (issue title = Card 1 headline):** The FTC Sued Hims &amp; Hers Over Its Ad Pixel and Its Billing
- **Byline:** By Jay Bell, Editor
- **Utility line:** [Read online]({{VIEW_ONLINE_LINK}}) &nbsp;|&nbsp; [Unsubscribe]({{UNSUBSCRIBE_LINK}})

**[IMAGE s0 — BANNER]** Branded masthead banner (helix emblem + wordmark + tagline lockup). Not a story photo. Text baked as real type, not AI-generated lettering.

---

## ===== GREETING + THESIS =====

**Good morning, operators.**

**Thesis line:** Every enforcement story this month landed on the front office &mdash; the ad pixel, the billing page, the intake form &mdash; not the exam room.

The regulators spent July reading funnels, not charts. Here is the week that matters for your business.

---

## ===== TABLE OF CONTENTS =====

*In today's issue:*

- The FTC sued Hims &amp; Hers &mdash; and the complaint reads like an audit checklist for your clinic
- The FDA's peptide panel voted. Six of seven got through. Why that is not the green light it looks like.
- The FDA's second wave of GLP-1 marketing letters: about 55 companies, one recurring phrase
- Your telehealth prescribing authority still expires December 31 &mdash; and the replacement rule still isn't written
- The "25 patients an hour" allegation against a Novo-endorsed telehealth partner
- The Compliance Desk: the exact phrases the FDA quoted back, and the safer way to say it

---

## ===== STORY CARD 1 (LEAD) =====

**CATEGORY LABEL:** FTC · PRIVACY &amp; BILLING

**HEADLINE (linked):** [The FTC Sued Hims &amp; Hers Over Its Ad Pixel and Its Billing](https://www.aol.com/articles/exclusive-us-ftc-suing-hims-163411000.html)

**[IMAGE s1]** Photorealistic editorial: a federal courthouse limestone facade shot low in hard daylight, or hands resting on a phone face-down on a desk in warm light. Text-safe, no legible signage or screens.

**The Short Version:** On July 29 the Federal Trade Commission &mdash; joined by the State of Utah and Los Angeles County &mdash; sued Hims &amp; Hers in federal court on two tracks: that it sent users' health information to ad platforms including Meta and Snap after promising privacy, and that it billed customers for prescriptions before they met a provider, inside subscriptions that were hard to cancel. Hims called the suit an effort to "generate headlines." The allegations are unproven.

**The Details:**
- Plaintiffs are the FTC, the State of Utah, and Los Angeles County; the suit was filed in federal court on July 29 (confirmed across two independent Reuters copies).
- The privacy count: the FTC says Hims shared customer health data with advertising companies two ways &mdash; by handing over lists of certain customers, and by third-party site tracking that automatically passed visitor "Events" to platforms named as Meta and Snap.
- The billing count: the FTC alleges Hims "started charging users for prescriptions before they have had a chance to meet with healthcare providers," most often right after an intake form, and made subscriptions "difficult to cancel."
- The statutes cited, as reported: the FTC Act and the Restore Online Shoppers' Confidence Act (ROSCA), which governs online subscription billing and cancellation; Utah and LA County add state consumer-protection claims. Hims shares fell sharply on the filing (Reuters reported roughly 12%; Bloomberg more than 15%).

**Why It Matters:** You do not need Hims' scale to be exposed to Hims' theory. The privacy count targets the exact setup most clinics run &mdash; a Meta or Snap pixel on a page that collects health intake &mdash; and the billing count targets the standard play of charging the moment an intake form is done. There is also a competitive read: the category leader now spends the back half of 2026 fighting regulators instead of taking your patients.

**Read more &rarr;** https://www.aol.com/articles/exclusive-us-ftc-suing-hims-163411000.html

---

## ===== STORY CARD 2 =====

**CATEGORY LABEL:** FDA · PEPTIDES

**HEADLINE (linked):** [The FDA's Peptide Panel Voted. Six of Seven Got Through.](https://time.com/article/2026/07/23/fda-committee-peptides/)

**[IMAGE s2]** Photorealistic editorial: an empty federal advisory-committee hearing room &mdash; rows of institutional chairs and gooseneck microphones, cool overhead light. Text-safe, no legible placards.

**The Short Version:** The FDA's Pharmacy Compounding Advisory Committee met July 23&ndash;24 and recommended adding six of the seven peptides on its docket to the Section 503A bulks list &mdash; the list that governs what state-licensed pharmacies may legally compound. The panel backed BPC-157, KPV, TB-500, MOTS-c, Semax, and Epitalon, and rejected only emideltide (DSIP). The votes overruled the FDA's own scientists, who had recommended against all seven.

**The Details:**
- Day 1 (July 23): BPC-157, KPV, and TB-500 each passed 8&ndash;6 with one abstention; MOTS-c passed 7&ndash;5 with two abstentions (Pharmaceutical Executive; TIME confirms the BPC-157 tally).
- Day 2 (July 24): Semax and Epitalon were recommended; emideltide (DSIP) was the panel's only rejection, failing 6&ndash;7 with one abstention (TIME).
- The recommendation is non-binding. A yes vote opens formal notice-and-comment rulemaking &mdash; a proposed rule, a comment period, then a final rule &mdash; which Pharmaceutical Executive put at a realistic 8 to 12 months out, running into 2027.
- STAT and NBC News both reported that a majority of the panelists who voted yes had ties to the peptide industry &mdash; a detail that shapes how much weight the FDA gives a non-binding recommendation.

**Why It Matters:** If your peptide line has sat in limbo since 2023, the panel just pointed at the door. It did not open it. Nothing about BPC-157 or TB-500 became legal to compound this week, and an operator who restocks or rewrites marketing copy on the strength of a non-binding vote is front-running a rule that does not exist yet &mdash; and may not for a year.

**Read more &rarr;** https://time.com/article/2026/07/23/fda-committee-peptides/

---

## ===== STORY CARD 3 (HOUSE ANNOUNCEMENT — native, byte-identical format) =====

> **BUILD FLAG:** This card is the house item. It must render with the SAME template, label style, image dimensions, bullet structure, and "Read more →" as every news card. Mention #1 of 2. `Read more →` links to the literal `https://medium.com/@ai_integraterz/the-paid-acquisition-playbook-is-closing-for-mens-health-clinics-here-is-the-one-that-isn-t-07172d95e2bb` placeholder. Image s3 must sit naturally among the news photos — not brighter, cleaner, or more "brand."

**CATEGORY LABEL:** PATIENT ACQUISITION

**HEADLINE (linked):** [Locked Out of Paid Ads, Men's-Health Operators Are Building Owned Acquisition Engines](https://medium.com/@ai_integraterz/the-paid-acquisition-playbook-is-closing-for-mens-health-clinics-here-is-the-one-that-isn-t-07172d95e2bb)

**[IMAGE s3]** Photorealistic editorial, matched to the news images in grain and light: a small clinic reception area or an operator's desk in early natural light &mdash; a chair, a landline, morning shadows. Text-safe, no legible screens or signage. Must not be the visual outlier.

**The Short Version:** Between platform bans on health creative and a widening enforcement lane on marketing copy, the paid-acquisition playbook is closing for men's-health and telehealth operators. A growing number are going the other way &mdash; building an owned engine out of assets they already have. AI Integraterz places a Go-to-Market Engineer inside the business to build exactly that: the dormant list, the unused network, and the referral channels turned into a patient pipeline the operator owns outright.

**The Details:**
- The premise: most clinics sit on three unconverted assets &mdash; a list they stopped emailing, a network they never systematized, and an audience they could borrow but never ask. Those are labor problems, not ad-budget problems.
- The model: a Go-to-Market Engineer embedded ~30&ndash;35 hours a week &mdash; in the clinic's tools, Slack, and context, like an employee &mdash; with AI Integraterz architecting the systems behind them. One flat monthly fee, salary included; no payroll, benefits, or HR.
- The engine: four pillars &mdash; Activate (dormant list and database), Own (network, partners, referrals), Find (podcasts, co-promoters, new audiences), and Build (a community and content that compound).
- The proof: a dormant-list reactivation for MoneyEDU produced 100 booked appointments with no new ad spend. The full men's-health write-up is the case study at aiintegraterz.com/case-studies/mens-health.pdf.

**Why It Matters:** Every other story in this issue narrows the paid lane &mdash; the FTC over pixels, the FDA over ad copy, the platforms over health creative. An owned channel is the one acquisition system a regulator or an algorithm cannot switch off. For a clinic, the target is defined in one currency, in writing, before the work starts: patients.

**Read more &rarr;** https://medium.com/@ai_integraterz/the-paid-acquisition-playbook-is-closing-for-mens-health-clinics-here-is-the-one-that-isn-t-07172d95e2bb

---

## ===== STORY CARD 4 =====

**CATEGORY LABEL:** FDA · ADVERTISING

**HEADLINE (linked):** [The FDA Sent a Second Wave of GLP-1 Marketing Letters. Same Phrases, New Companies.](https://www.raps.org/resource/fda-cites-companies-for-cgmp-violations-telehealth-firms-for-illegally-marketing-glp-1-drugs.html)

**[IMAGE s4]** Photorealistic editorial: gloved hands over a stainless compounding tray with unbranded amber glassware, clinical side light. Text-safe, no labels in frame.

**The Short Version:** The 30 warning letters the FDA sent telehealth companies in March were not the end of it. In June the agency posted a second wave &mdash; about 25 more &mdash; over the same conduct: marketing copy for compounded GLP-1 products that implied FDA approval or equivalence to the branded drugs, and branding that hid who actually compounded the product. The letters target the website and the funnel, not the compounding itself.

**The Details:**
- March 3, 2026: 30 letters. The FDA's cited categories (Foley &amp; Lardner): putting the firm's own brand on labels so it looks like the compounder when it isn't; marketing that doesn't qualify for the 503A or 503B exemptions; claims implying the FDA approved or evaluated the compounded product.
- The exact phrases the FDA quoted back (Foley): "Generic Zepbound," "Contains the active pharmaceutical ingredient in Wegovy," "This FDA-approved treatment promotes safe, effective weight loss," and "FDA approved active pharmaceutical ingredients."
- June 2026: about 25 more letters, issued around June 8 and posted June 16, for false or misleading claims about compounded semaglutide and tirzepatide (RAPS); companies were given 15 business days to respond.
- The FDA's stated escalation, across both waves: failure to correct may bring enforcement including seizure or injunction, and foreign firms' products may be detained at the border (Foley).

**Why It Matters:** Two waves in four months is the pattern, and it lives in a lane most clinical teams never touch &mdash; the marketing copy. The exposure sits with whoever writes the site, the ad, and the funnel. Any operator still describing a compounded product by pointing at a brand-name drug is using the exact language the FDA has now quoted back at about 55 companies.

**Read more &rarr;** https://www.raps.org/resource/fda-cites-companies-for-cgmp-violations-telehealth-firms-for-illegally-marketing-glp-1-drugs.html

*(Secondary source for the March wave and the quoted phrases: Foley &amp; Lardner — https://www.foley.com/p/102mmr0/glp1-compliance-fda-targets-telehealth-marketing-in-30-new-warning-letters/)*

---

## ===== STORY CARD 5 =====

**CATEGORY LABEL:** DEA · TELEHEALTH

**HEADLINE (linked):** [Your Telehealth Prescribing Authority Still Expires December 31](https://www.hklaw.com/en/insights/publications/2026/01/dea-and-hhs-extend-telemedicine-prescribing-flexibilities-through-2026)

**[IMAGE s5]** Photorealistic editorial: an empty, sunlit exam room &mdash; paper-covered table, a shaft of afternoon light, unbranded. Text-safe, no legible charts or posters.

**The Short Version:** The pandemic-era rule that lets practitioners prescribe controlled substances by telemedicine without an initial in-person exam is still the operating law &mdash; and still set to lapse on December 31, 2026. No permanent replacement has been finalized. Testosterone and its esters are Schedule III, so this rule governs telehealth TRT prescribing directly.

**The Details:**
- The current flexibility covers Schedule II&ndash;V prescribing by telemedicine with no initial in-person exam required, from January 1 through December 31, 2026 (Holland &amp; Knight).
- This is the fourth temporary extension; the DEA says it intends to issue final regulations before the deadline and is still reviewing comments on the proposed permanent rules.
- The extension added no new documentation, registration, or technology requirement &mdash; the operating rules didn't change, only the clock kept running.
- Both the agency and its counsel frame the extension as a bridge meant to avoid a "telemedicine cliff."

**Why It Matters:** Every telehealth TRT business is running on a permission slip with about five months left on it, and the rule that replaces it isn't written. A permanent framework could add platform-level or prescriber-level registration that does not exist today. This is the single largest structural unknown on the calendar for remote-prescribing operators &mdash; and it has a hard date.

**Read more &rarr;** https://www.hklaw.com/en/insights/publications/2026/01/dea-and-hhs-extend-telemedicine-prescribing-flexibilities-through-2026

---

## ===== STORY CARD 6 =====

**CATEGORY LABEL:** TELEHEALTH · OVERSIGHT

**HEADLINE (linked):** [A Novo-Endorsed Telehealth Partner Is Accused of Running a Volume Machine](https://www.statnews.com/2026/07/20/lifemd-weight-loss-drugs-novo-nordisk-telemedicine/)

**[IMAGE s6]** Photorealistic editorial, distinct from every other slot: a tight overhead flat-lay of a dense stack of unlabeled manila folders and a cooling coffee on a clinic desk &mdash; the texture of volume. Text-safe, nothing legible.

**The Short Version:** STAT reported on July 20 that LifeMD &mdash; a publicly traded telehealth firm Novo Nordisk lists as a recommended GLP-1 partner &mdash; pushed clinicians to see more patients and prescribe faster, with thin screening and follow-up. The reporting rests on five former employees and two lawsuits from former leaders. LifeMD strenuously denies it; its CEO says the company is not a "pill mill." The allegations are unproven.

**The Details:**
- The central allegation: providers "at times were expected to review the cases of 25 people per hour based only on electronic forms" (STAT, via broadcast syndication).
- Former staff say the company "provided little screening and follow-up" and discouraged providers from asking questions they felt were medically relevant, so as not to "delay care."
- The reporting draws on five former employees and two lawsuits filed by former top leaders; LifeMD strenuously denies the allegations, and CEO Justin Schreiber said, "Our objective has not been to run a pill mill."
- Novo Nordisk lists LifeMD on its website as offering "legitimate medicine sourcing and patient support," and expanded that partnership in January 2026 to include oral Wegovy.

**Why It Matters:** The number that gets quoted will be 25 chart reviews an hour on forms alone &mdash; the line between a defensible intake and an indefensible one. It also kills a comfortable assumption: a manufacturer's endorsement is not a compliance shield, because being on Novo's partner list did not keep LifeMD out of the story. For any clinic that runs real consults and follow-up, that contrast is now documentable.

**Read more &rarr;** https://www.statnews.com/2026/07/20/lifemd-weight-loss-drugs-novo-nordisk-telemedicine/

---

## ===== UTILITY SEGMENT =====

**SECTION DIVIDER LABEL:** THE COMPLIANCE DESK

**Title:** The GLP-1 marketing phrases the FDA quoted back at about 55 companies &mdash; and the safer way to say it

**[IMAGE s7]** Photorealistic macro: a red felt-tip pen resting on a plain, blank sheet of paper, shallow depth of field, natural light. Text-safe, nothing legible.

**Intro:** The enforcement in today's first and fourth stories lives in your marketing copy, not your clinical work. Here is a five-minute audit you can run on your own site this afternoon. It is an editorial summary of what the FDA actually cited &mdash; not legal advice.

**Run each line against your site, ads, and funnel:**

1. **Flagged:** "Generic Zepbound" or "Contains the active pharmaceutical ingredient in Wegovy."
   **The problem:** implies your compounded product is equivalent to, or interchangeable with, an FDA-approved drug &mdash; a category the FDA cited.
   **Safer register:** describe a compounded preparation on its own terms; stop defining it by reference to a brand-name drug.

2. **Flagged:** "This FDA-approved treatment promotes safe, effective weight loss" or "FDA approved active pharmaceutical ingredients."
   **The problem:** implies the FDA approved or evaluated the compounded product. It did not &mdash; compounded drugs are not FDA-approved, which is why these exact lines drew letters.
   **Safer register:** never attach "FDA-approved" to a compounded product, full stop.

3. **Flagged:** your own brand on the label in a way that suggests you compound the drug when you don't.
   **The problem:** one of the three cited categories &mdash; it obscures who actually compounded the product.
   **Safer register:** name the compounding pharmacy plainly; don't let house branding stand in for the compounder. If a prospect asks who compounds your product, you should be able to answer in one sentence.

4. **Flagged:** promotion that doesn't qualify for the 503A or 503B exemptions.
   **The problem:** the second cited category &mdash; marketing that treats a compounded product like a mass-market approved drug.
   **Safer register:** keep every claim inside the compounding context; drop the "approved drug" framing entirely.

**The one-line rule (per Foley &amp; Lardner's read of the letters):** avoid implying "equivalence, interchangeability with, or approval in the same manner as FDA-approved products," and scrub the page for unsubstantiated weight-loss claims.

**The point:** none of this touches your clinical protocol. It is the copy on the page &mdash; which, per today's first and fourth stories, is exactly where the enforcement is.

---

## ===== HOUSE BLURB (mention #2 of 2 — final) =====

The Protocol is published by AI Integraterz. We build owned patient-acquisition engines for men's-health and telehealth operators &mdash; the one channel a platform ban or a warning letter can't switch off. If this issue has you counting how much of your pipeline rides on paid ads, that's the conversation: aiintegraterz.com.

---

## ===== KEEP READING =====

**SECTION LABEL:** Keep Reading

*(Three teasers, seeded with real verified sources until back issues exist. MyClaw style: headline + "Plus:" subline + link.)*

1. **[The FDA's Move to Close the 503B GLP-1 Door](https://www.orrick.com/en/Insights/2026/05/FDA-Moves-to-Shut-the-Door-on-Large-Scale-Compounding-of-GLP1-Drugs)**
   Plus: the proposal is in comment review, no final rule yet &mdash; and the finalization date is the operator's blind spot.

2. **[Med Spas Kept Selling After the Shortage Ended](https://www.healio.com/news/endocrinology/20260717/compounded-semaglutide-tirzepatide-continued-to-be-sold-after-shortages-ended)**
   Plus: a JAMA Health Forum study found nearly 1 in 5 supplying pharmacies lacked sterile-compounding authorization &mdash; the risk you inherit.

3. **[45 of 49 Online Sellers Issued a Prescription &mdash; Most Within a Day](https://www.statnews.com/2026/07/06/glp-1-telehealth-prescriptions-jama-yale-secret-shopper-study/)**
   Plus: only 27% required a video visit before prescribing &mdash; the number every future rulemaking will quote.

---

## ===== SIGN-OFF =====

Until next week &mdash;

**Jay Bell**
Editor, The Protocol

*Reply and tell me what you're seeing on the ground. I read every response.*

---

## ===== FOOTER =====

**Primary-tab ask:** Want The Protocol to keep landing where you'll see it? Drag this email to your Primary tab.

**Disclaimer:** The Protocol is written for business owners and operators. It reports on business, regulatory, and market developments and is not medical, legal, or investment advice.

**Publisher (legal identification):**
AI Integraterz
37460 Beacon Brick Road, Zephyrhills, Florida 33541

[View this email online]({{VIEW_ONLINE_LINK}}) &nbsp;|&nbsp; [Unsubscribe]({{UNSUBSCRIBE_LINK}})

*Too frequent, or not a fit? Reply and tell us, or unsubscribe above &mdash; no hard feelings.*

---
---

# FACT-TRACE APPENDIX (QA — not part of the email)

Every card mapped to its source. Card body facts are drawn only from the research files below; no facts added.

| Slot | Story | Primary source (Read more link) | Research file |
|---|---|---|---|
| Card 1 (LEAD) | FTC sues Hims &amp; Hers (privacy + billing), filed Jul 29 | Reuters via AOL — https://www.aol.com/articles/exclusive-us-ftc-suing-hims-163411000.html | `stories-fresh.md` §1 |
| Card 2 | PCAC recommended 6 of 7 peptides for 503A bulks list | TIME — https://time.com/article/2026/07/23/fda-committee-peptides/ | `stories-verified.md` §1 |
| Card 3 | HOUSE — owned acquisition engine (Fractional GTM) | `https://medium.com/@ai_integraterz/the-paid-acquisition-playbook-is-closing-for-mens-health-clinics-here-is-the-one-that-isn-t-07172d95e2bb` (literal placeholder) | `OFFER-fractional-gtm.md` + case study aiintegraterz.com/case-studies/mens-health.pdf |
| Card 4 | Second wave of GLP-1 marketing warning letters (~55 total) | RAPS — https://www.raps.org/resource/fda-cites-companies-for-cgmp-violations-telehealth-firms-for-illegally-marketing-glp-1-drugs.html (+ Foley secondary) | `stories-verified.md` §4 |
| Card 5 | DEA telehealth prescribing flexibilities expire Dec 31, 2026 | Holland &amp; Knight — https://www.hklaw.com/en/insights/publications/2026/01/dea-and-hhs-extend-telemedicine-prescribing-flexibilities-through-2026 | `stories-verified.md` §3 |
| Card 6 | LifeMD volume-machine allegations (Novo partner) | STAT — https://www.statnews.com/2026/07/20/lifemd-weight-loss-drugs-novo-nordisk-telemedicine/ | `stories-fresh.md` §2 |
| Utility | Marketing-copy compliance checklist (quoted phrases) | Foley — https://www.foley.com/p/102mmr0/glp1-compliance-fda-targets-telehealth-marketing-in-30-new-warning-letters/ | `stories-verified.md` §4 |
| Keep Reading 1 | 503B GLP-1 proposal | Orrick (real, verified) | `stories-verified.md` §2 |
| Keep Reading 2 | Med-spa secret-shopper study | Healio (real, verified) | `stories-verified.md` §5 |
| Keep Reading 3 | Yale online-seller study (45/49; 27% video) | STAT (real, verified) | `RESEARCH-MENS-HEALTH-NEWSLETTER.md` §6 |

**Litigation/allegation fairness:** Card 1 (Hims) and Card 6 (LifeMD) both state the company denial and label the claims unproven, per the research files' explicit instruction to report as allegations, not facts.

**Stories considered and left OUT (reserved for issue #2):**
- **503B GLP-1 proposal** (`stories-verified.md` §2) — a status update, not an event ("still a proposal, comments closed Jun 29, no change"), and it overlaps the GLP-1/FDA ground already covered by Card 4. Used instead as Keep Reading #1.
- **Med-spa "weak link" study** (`stories-verified.md` §5) — strong, but its compounding-supply-chain angle is adjacent to Cards 2 and 4, and it's the least "this week" of the set (fieldwork Aug–Oct 2025). Card 6 (LifeMD) was chosen over it for freshness, a named public company, and a distinct oversight/operations angle. Used instead as Keep Reading #2.

**House mention count:** 2 (Card 3 + House Blurb). Footer publisher line = legal identification, not counted.
**Banned words:** none. **Emojis in rendered copy:** none (brand mark is a drawn helix emblem).
