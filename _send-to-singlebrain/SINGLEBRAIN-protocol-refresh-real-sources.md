# → SingleBrain: The Protocol -- fix the dead links AND the redundant content

The revised Protocol did NOT pass QA. Two problems.

## Problem 1: both FDA links are dead (404), and your ledger certified them as "200"
- Card 1 -> `https://www.fda.gov/drugs/drug-alerts-and-statements/fda-issues-class-wide-labeling-changes-testosterone-products` -> **HTTP 404**
- Card 2 -> `https://www.fda.gov/drugs/postmarket-drug-safety-information-patients-and-providers/testosterone-information` -> **HTTP 404**

Both were fetched and both return 404 -- the pages do not exist. Your ledger logged both as "HTTP Status: 200, re-verified 2026-08-04." That is false, and it's the second time a dead link was certified as 200.

**Hard rule from now on: a source is "verified" ONLY if a live fetch returns HTTP 200 AND you can quote a specific sentence from the live page body.** A 404, a redirect to a homepage, or a page that reads "Page Not Found" is NOT verified -- do not use it and never log it as 200. If you cannot open the page and read the supporting sentence, that source does not exist for our purposes.

## Problem 2: three of the four cards are the same story
Card 1 (FDA removes the boxed warning), Card 2 (the TRAVERSE trial behind that FDA action), and Card 4 (a prescribing rebound attributed to that same Feb-2025 change) all revolve around one 18-month-old regulatory event. That is repetitive and stale for a "Latest Developments" briefing.

## The fix
- **Keep Card 3 (the native referral card) and Card 4 (Epic Research prescribing data -- it is fresh, July 2026, and verified). Do not change those.**
- The FDA / testosterone-labeling story may appear in **at most ONE card**, and only with a **real, working, fetch-verified link** -- find the actual live FDA page, or use the NEJM TRAVERSE paper; confirm HTTP 200 + a quotable sentence on the live page.
- **Replace the other card with a DISTINCT, CURRENT men's-health-industry story** -- ideally published in the last ~60 days -- from a real, fetch-verified source. Choose a different angle a clinic or coaching operator cares about (clinic operations/business, the telehealth men's-health market, a funding or M&A move, a new clinical study, a payer/regulatory update other than the Feb-2025 one). NOT another angle on the same FDA event.
- Every source in the issue: fetch it, confirm 200, and record the exact supporting quote from the live page.

Deliver: the updated Protocol HTML + a source ledger (final URL, HTTP status, publication date, exact live-page quote) for every card. Do NOT send anything.
