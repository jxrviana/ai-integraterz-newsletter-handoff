# The People Person -- Issue 001 -- Verified Source Ledger

**Date:** August 3, 2026
**Revised HTML:** `/opt/data/newsletter-review-packages/html/the-people-person-issue-001-revised.html`

All URLs below were fetched via HTTP GET (`curl -sL` with browser User-Agent) on 2026-08-03. Non-200 statuses are recorded honestly.

---

## STORY CARD 1 -- AI-Generated Applications and Structured Screening (HIRING TECHNOLOGY)

| Field | Value |
|---|---|
| **Final URL** | https://www.shrm.org/topics-tools/news/hire-smarter-fairer-age-of-ai-generated-applications |
| **HTTP Status** | 200 |
| **Publisher** | SHRM (Society for Human Resource Management) |
| **Author** | Eric House |
| **Date** | September 2025 (dateModified: 2025-09-21) |
| **Key Supporting Sentence** | "AI-generated resumes are flooding recruiters. Learn how structured AI interviews cut through the noise, boost fairness, and help HR teams hire smarter at scale." |
| **Extraction Method** | JSON-LD schema.org NewsArticle `description` field in page source |
| **Replaced URL** | https://www.staffingindustry.com/editorial/daily-news/ai-job-scams-push-employers-into-digital-identity-checks |
| **Replacement Reason** | HTTP 403 (blocked by Cloudflare CDN) |

---

## STORY CARD 2 -- New York Ghost Job Posting Legislation (REGULATION)

| Field | Value |
|---|---|
| **Final URL** | https://www.shrm.org/topics-tools/news/talent-acquisition/new-york-law-ghost-job-postings |
| **HTTP Status** | 200 |
| **Publisher** | SHRM (Society for Human Resource Management) |
| **Author** | Roy Maurer |
| **Date** | July 24, 2026 (dateModified: 2026-07-24) |
| **Key Supporting Sentence** | "New York lawmakers advance a bill requiring employers to disclose whether job openings are real, with steep fines for misleading or outdated postings." |
| **Extraction Method** | JSON-LD schema.org NewsArticle `description` field in page source |
| **Replaced URL** | https://www.forbes.com/sites/forbesstaffing/2026/08/02/americas-best-recruiting-temp-staffing-firms-2026/ |
| **Replacement Reason** | HTTP 404 (permanently dead -- confirmed non-functional, must not be reused) |

---

## STORY CARD 3 -- Native Card: Referral Channel Engineering (TALENT SYSTEMS)

| Field | Value |
|---|---|
| **Final URL (Short)** | https://medium.com/p/f7d99f4f2f10 |
| **HTTP Status** | **403 Forbidden** (blocked by Medium CDN/Cloudflare; browser access may differ) |
| **Article Facts Used** | User-provided only: operationalization problem, $13.81B 2026 affiliate-spend forecast, Power of Eight, Tracking, Terms, Follow-through |
| **Medium Link Usage** | Read-more link only. No article text reproduced. |
| **Native Card Affiliate Mention** | Exactly once, semantic, in WHY IT MATTERS paragraph |
| **CTA URL** | Not present in native card. CTA only in House Blurb section. |

---

## STORY CARD 4 -- White House Workforce Development Strategy (WORKFORCE POLICY)

| Field | Value |
|---|---|
| **Final URL** | https://www.shrm.org/topics-tools/news/trump-workforce-development-strategy |
| **HTTP Status** | 200 |
| **Publisher** | SHRM (Society for Human Resource Management) |
| **Date** | August 2025 (dateModified: 2025-08-19) |
| **Key Supporting Sentence** | "President Trump's new workforce strategy aims to expand work-based learning, connect Americans to in-demand jobs, and prepare workers for the AI-driven economy." |
| **Extraction Method** | JSON-LD schema.org NewsArticle `description` field in page source |
| **Replaced URLs** | https://www.staffingindustry.com/editorial/daily-news/uk-recruitment-market-gains-momentum-in-q2-boosted-by-it (HTTP 403) and https://www.staffingindustry.com/editorial/daily-news/australian-employers-boost-hiring-as-difficulties-ease (HTTP 403) |
| **Replacement Reason** | Both blocked by Cloudflare CDN |

---

## URL VERIFICATION LOG

All checks performed 2026-08-03 using `curl -sL -o /dev/null -w "HTTP %{http_code}" -A "Mozilla/5.0..."`:

| URL | HTTP Status | Notes |
|---|---|---|
| https://www.shrm.org/topics-tools/news/hire-smarter-fairer-age-of-ai-generated-applications | 200 | Used in revised Story Card 1 |
| https://www.shrm.org/topics-tools/news/talent-acquisition/new-york-law-ghost-job-postings | 200 | Used in revised Story Card 2 |
| https://medium.com/p/f7d99f4f2f10 | 403 | Used as read-more only in native Story Card 3 |
| https://www.shrm.org/topics-tools/news/trump-workforce-development-strategy | 200 | Used in revised Story Card 4 |
| https://www.forbes.com/sites/forbesstaffing/2026/08/02/americas-best-recruiting-temp-staffing-firms-2026/ | 404 | DEAD -- not reused |
| https://www.staffingindustry.com/editorial/daily-news/ai-job-scams-push-employers-into-digital-identity-checks | 403 | Blocked by Cloudflare |
| https://www.staffingindustry.com/editorial/daily-news/uk-recruitment-market-gains-momentum-in-q2-boosted-by-it | 403 | Blocked by Cloudflare |
| https://www.staffingindustry.com/editorial/daily-news/australian-employers-boost-hiring-as-difficulties-ease | 403 | Blocked by Cloudflare |

---

## CTA / AFFILIATE LINK AUDIT

| Field | Value |
|---|---|
| **CTA URL** | https://whimsy-nebula-47ch.here.now/ |
| **Visible Text** | "See the affiliate program →" |
| **Placement** | House Blurb section only (after soft bridge text) |
| **Occurrences in Visible HTML** | Exactly 1 |
| **Presence in Native Card (Card 3)** | None |

---

## CORRECTION BRIEF COMPLIANCE

| Requirement | Status |
|---|---|
| Byline: Carson Greer | PASS |
| Signoff: Carson Greer, Editor, The People Person | PASS |
| From: The People Person <the-people-person@send.usingaitoscale.com> | PASS |
| Reply-To: xander@usingaitoscale.com | PASS |
| Address: 37460 Beacon Brick Road, Zephyrhills, Florida 33541 | PASS |
| Neutral cold-outbound footer line | PASS |
| CTA: "See the affiliate program →" exactly once | PASS |
| Soft house blurb bridge | PASS |
| Native card semantic affiliate mention exactly once | PASS |
| Medium read-more only in native card | PASS |
| Rating: The People Person feedback: Nailed it / Average / Needs work | PASS |
| Only {{ MessageURL }} and {{ UnsubscribeURL }} tags | PASS |
| No AI Integraterz/Integraterz | PASS |
| No emoji, no em dash | PASS |
| No social/opt-in links | PASS |
| No placeholders | PASS |
| 4 unique text-free image prompts | PASS |
| Source ledger in HTML comments | PASS |
| 600px layout preserved | PASS |
| Four identical story cards | PASS |
| Native card at position 3 | PASS |
| Old Forbes URL NOT reused | PASS |
| Medium 403 recorded honestly | PASS |
| No other newsletters modified | PASS |
