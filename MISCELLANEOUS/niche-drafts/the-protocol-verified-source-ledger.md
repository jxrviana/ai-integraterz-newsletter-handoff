# The Protocol Issue 001 -- Verified Source Ledger
## Generated: 2026-08-04
## Re-verified: 2026-08-04 via browser HTTP fetch

---

### SOURCE VERIFICATION METHODOLOGY
Final customer-facing URLs were rechecked in the browser environment on 2026-08-04. A source is verified only where the live page returned HTTP 200 and the exact supporting sentence was visible in the page body. Any source not meeting both conditions is marked blocked or unverified. No Google News redirect URLs, guessed slugs, or unverified homepages are used.

---

## STORY CARD 1 -- FDA Testosterone Label Changes (REGULATORY)

| Field | Value |
|---|---|
| **Final URL** | https://www.fda.gov/drugs/drug-alerts-and-statements/fda-issues-class-wide-labeling-changes-testosterone-products |
| **HTTP Status** | 200 |
| **Response Size** | ~45 KB |
| **Publication Date** | February 28, 2025 |
| **Publisher** | U.S. Food and Drug Administration |
| **Exact Supporting Sentence** | "Today, FDA informed sponsors of testosterone products about new labeling changes following the agency's review of the findings from the Testosterone Replacement Therapy for Assessment of Long-term Vascular Events and Efficacy Response in Hypogonadal Men (TRAVERSE) clinical trial and the results from required postmarket ambulatory blood pressure (ABPM) studies." |
| **Exact Supporting Sentence 2** | "Led by the TRAVERSE trial's results, FDA is recommending changes to current labeling language, to include: adding the results of the TRAVERSE trial to all testosterone products; retaining 'Limitation of Use' language for age-related hypogonadism; and removing language from the Boxed Warning related to an increased risk of adverse cardiovascular outcomes for all testosterone products." |
| **Exact Supporting Sentence 3** | "Results from the TRAVERSE trial were submitted in 2023, concluding that there was no increase in the risk of adverse cardiovascular outcomes in men using testosterone for hypogonadism." |
| **Exact Supporting Sentence 4** | "Results from the completed ABPM studies confirmed an increase in blood pressure with use of all testosterone products, class-wide." |
| **Wording Permitted** | Yes -- public domain U.S. government work. Attribution to FDA required. |

### Previously Suspect/Replaced Sources (NOT USED)
- Miami Herald article280705845.html: HTTP error (curl exit code 92, connection failed)
- HHS.gov press release URL: 403 Forbidden
- Both removed per user instruction.

---

## STORY CARD 2 -- Pentagon Testosterone Screening Plan (CLINICAL)

| Field | Value |
|---|---|
| **Final URL** | https://www.pbs.org/newshour/health/as-hegseth-pursues-a-high-t-military-heres-what-to-know-about-testosterone-replacement |
| **HTTP Status** | 200 |
| **Response Size** | Browser page body visible |
| **Publication Date** | July 26, 2026 |
| **Publisher** | PBS News / PolitiFact |
| **Author** | Madison Czopek |
| **Exact Supporting Sentence 1** | "But when it comes to testosterone levels, optimization isn't so straightforward. Scientists don't agree on a single value that is too low." |
| **Exact Supporting Sentence 2** | "A July 15 Pentagon spokesperson statement confirmed the testosterone deficiency screening Hegseth spoke about would be mandatory for all active duty and reserve personnel 30 and older." |
| **Exact Supporting Sentence 3** | "Not everyone who receives one blood test showing lower testosterone levels needs testosterone replacement therapy, which can have benefits but also comes with risks." |
| **Wording Permitted** | Yes -- attributed reporting; not clinical guidance. |

### Previously Suspect/Replaced Sources (NOT USED)
- CNBC article: 403 Forbidden (curl blocked by CDN)
- Reuters article: 401 Unauthorized (paywall/auth wall)
- Time Magazine: 406 Not Acceptable
- All DoD/military.com URLs tested: 404 Not Found
- Retired from the final issue because Card 2 now uses a distinct current clinical/operations story from PBS News.

---

## STORY CARD 3 -- Native Card: Referral Channel Engineering (CLINIC GROWTH)

| Field | Value |
|---|---|
| **Final URL (Short)** | https://medium.com/p/f7d99f4f2f10 |
| **HTTP Status** | 403 Forbidden |
| **Response Size** | 0 (blocked by Medium CDN) |
| **Honest Assessment** | Medium's CDN returned 403 when fetched via curl from this environment. The article URL could not be verified by automated HTTP GET. |

### User-Provided Article Facts (Used for Native Card Content)
Per user correction brief, the following facts are incorporated into the native card:

1. **Operationalization Problem**: Most clinics treat referrals as passive hope; referral volume is an engineering problem, not a marketing problem.
2. **$13.81B 2026 Affiliate-Spend Forecast**: The affiliate marketing industry is projected to reach $13.81 billion in spending in 2026, contextualizing the opportunity for structured referral channels.
3. **Power of Eight**: Eight strategic referral sources, properly engineered, can sustain a clinic's new-patient pipeline.
4. **Tracking**: Without tracking which referral source produced each new patient, the channel cannot be optimized.
5. **Terms**: Clear terms (what the referrer gets, what the referred patient gets) eliminate ambiguity and increase conversion.
6. **Follow-through**: A monthly referral roundup email closes the feedback loop and keeps referrers engaged.

### Wording Permitted
The Medium article is cited as a read-more link only. The native card copy is original newsletter editorial referencing the article's publicly described framework. No Medium paywall content is reproduced.

---

## STORY CARD 4 -- Testosterone Prescribing Rebound (PRESCRIBING)

| Field | Value |
|---|---|
| **Final URL** | https://epicresearch.org/articles/after-nearly-a-decade-long-decrease-testosterone-prescribing-rates-rising-again |
| **HTTP Status** | 200 |
| **Response Size** | ~233 KB (Next.js rendered page) |
| **Publication Date** | July 29, 2026 |
| **Authors** | Kersten Bartelt, RN and Caleb Cox |
| **Publisher** | Epic Research (Cosmos Study) |
| **Exact Supporting Sentence 1** | "The share of male patients prescribed testosterone fell from 0.83% in 2013 to 0.64% by 2021. It then rose to 0.93% in 2025 and reached 0.95% in the partial first half of 2026." |
| **Exact Supporting Sentence 2** | "The growth was broad: every age group 30 and older surpassed its early-2010s peak by 2025. Men aged 50-64 had the highest prevalence at 1.57% in 2025, while those 18-29 had the lowest at 0.14%." |
| **Exact Supporting Sentence 3** | "Testosterone replacement therapy is prescribed to treat low testosterone (low T) levels, also known as hypogonadism. Prescribing rose sharply in the United States through the 2000s and early 2010s..." |
| **Exact Supporting Sentence 4** | "However, in February 2025, the FDA removed the boxed cardiovascular warning from all testosterone products after the 2023 TRAVERSE trial found testosterone therapy was not associated with an increased risk for major adverse cardiac events among men with hypogonadism and elevated cardiovascular risk." |
| **Wording Permitted** | Yes -- Epic Research articles are publicly accessible and citable. Attribution to Epic Research / Cosmos Study required. |

### Note on "Suspect" Status
User flagged Epic Research as a "known old source." However, this article was published July 29, 2026, and was verified via HTTP 200 with complete content extraction. The data comes from Cosmos, a dataset of 310+ million patient records from 2,000+ hospitals and 49,000+ clinics. All numbers quoted above are extracted directly from the live page, not from any secondary summary.

---

## ADDITIONAL URL ATTEMPTS (Honest Failure Log)

| URL | HTTP Status | Notes |
|---|---|---|
| https://www.miamiherald.com/news/health-wellness/article280705845.html | 000 (curl error 92) | Connection failed |
| https://www.cnbc.com/2026/07/20/testosterone-replacement-therapy-us-military-plans-to-test-troops.html | 403 | Blocked by CDN |
| https://www.reuters.com/business/healthcare-pharmaceuticals/doctors-question-evidence-behind-pentagon-plan-testosterone-screening-2026-07-18/ | 401 | Auth/paywall |
| https://www.hhs.gov/about/news/2026/06/18/hhs-announces-requested-updates-testosterone-therapy-product-labels.html | 403 | Blocked |
| https://www.nytimes.com/2026/05/12/well/testosterone-treatment-men.html | 403 | Blocked |
| https://www.forbes.com/sites/forbesbusinesscouncil/2026/02/20/the-mens-wellness-clinics-scaling-a-new-concierge-like-model/ | 404 | Not found |
| https://www.statnews.com/2026/03/12/momentum-builds-for-federal-office-of-mens-health/ | 404 | Not found |
| https://www.theatlantic.com/health/archive/2026/01/testosterone-maxxing-has-gone-too-far/681465/ | 200 (redirected to unrelated article) | Wrong content |
| https://www.businessinsider.com/testosterone-overprescribed-men-who-should-take-it-backfires-2026-6 | 404 | Not found |
| https://time.com/7205746/military-testosterone-testing-policy/ | 406 | Not acceptable |
| https://www.endocrine.org/news-and-advocacy/news-room/2025/fda-removes-boxed-warning-on-testosterone | 200 (but page shows "Page Not Found") | Content missing |
| https://www.medium.com/p/f7d99f4f2f10 | 403 | Blocked by Medium CDN |
| https://www.fda.gov/drugs/postmarket-drug-safety-information-patients-and-providers/testosterone-information | 200 | Retired from Card 2 because it duplicated Card 1's FDA/TRAVERSE subject; not used in final HTML |

---

## SUMMARY

| Story Card | Source | HTTP Status | Verdict |
|---|---|---|---|
| Card 1: FDA Label Changes | FDA.gov | 200 | VERIFIED |
| Card 2: Pentagon Testosterone Screening Plan | PBS News / PolitiFact | 200 | VERIFIED -- distinct current story; exact quotes visible |
| Card 3: Referral Engineering (Native) | Medium | 403 | BLOCKED -- using user-provided facts |
| Card 4: Prescribing Rebound | Epic Research | 200 | VERIFIED |
