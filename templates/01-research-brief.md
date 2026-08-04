# Stage 1 â€” Research Brief (template)

## FILL THESE IN FIRST

*(Operator note, safe to leave in the pasted prompt.)*

| Placeholder | What to put in it | Where to get it |
|---|---|---|
| `{{NICHE}}` | The industry the newsletter serves, in plain words. e.g. `men's health businesses`, `recruiting and staffing firms`, `HVAC contractors` | `CLAUDE.md`, "The Five Newsletters" table |
| `{{AUDIENCE_DESCRIPTION}}` | Who exactly reads it, by job. e.g. `Owners and operators â€” clinic owners and medical directors, peptide/telehealth brand founders, and performance coaches` | Same table, plus whatever the client has said about the list |
| `{{CONTENT_PILLARS}}` | The 5-7 subject areas the issue must spread across, numbered. e.g. `1. Regulatory weather 2. Market and business 3. Clinical/product 4. Acquisition and retention 5. Tech and AI 6. Case story` | Reuse the pillar set from a prior `RESEARCH-*.md` for a comparable niche, or write it fresh from the niche's real concerns |
| `{{OUTPUT_FILE}}` | Absolute path for the research file. e.g. `C:\Users\Xander\Claude\Cowork\AI Integraterz\Newsletter\RESEARCH-SOLAR-NEWSLETTER.md` | Naming convention: `RESEARCH-<NICHE>-NEWSLETTER.md` in the working directory |

---

## PASTE FROM HERE

You are researching story candidates for an outbound trade newsletter serving **{{NICHE}}**.

**Audience:** {{AUDIENCE_DESCRIPTION}}. Address them as operators â€” people who run the business, sign the cheques, and carry the risk. Never as "subscribers," "friends," or consumers.

**Your output is not the newsletter.** It is the evidence file an editor writes from. It has to be strong enough that every number in the finished issue can be traced back to a line in your file, and every caveat you record survives into the issue.

### Deliverable

Write **{{OUTPUT_FILE}}** containing **10-12 story candidates**, plus the summary sections listed below. Nothing else. Do not draft newsletter copy.

### Hard rules â€” these are not preferences

1. **Fetch and verify every source.** Do not cite a URL you have not opened. Record the date you fetched it. A search-result snippet is not a source; it is a lead you still have to check.
2. **Prefer authoritative trade and primary sources.** Primary documents first (filings, peer-reviewed papers, regulator notices, official policy pages, government data). Then established trade press and named professional-services analysis. Everything else is a fallback you must justify.
3. **Reject content-farm statistics.** SEO stat listicles that recycle each other's figures without a study, sample, or date are the dominant failure mode in most niches. Reject them by name in your report, even when the number is plausible and convenient.
4. **Reject vendor marketing figures presented as research.** A benchmark self-published by a company that sells the thing being benchmarked is a marketing asset. If the sample size is undisclosed or tiny, say so. If you use one at all, label it "vendor research" in the entry itself, not just in a footnote.
5. **Flag every secondary source explicitly.** If the fact comes from a law firm's analysis of a Federal Register notice rather than the notice, write **Secondary** in the entry and name what blocked the primary (403, paywall, bot check). Two independent secondary sources agreeing is acceptable and must still be labelled.
6. **No fabricated numbers.** Not one. Do not estimate, do not round a range into a single figure, do not carry a number forward from memory. If a figure cannot be verified, either omit it or state plainly that it could not be verified.
7. **Chase the number to its origin.** When a striking figure is attributed to a named study, open the study. If the attribution turns out not to exist upstream, report the fabrication â€” that finding is more valuable than the number would have been.
8. **Work only inside the newsletter working directory.** Never read or search `Downloads`, `Desktop`, `Documents`, or anywhere else on the machine. Web fetching is expected; local file wandering is not.

### Coverage

Spread the candidates across these pillars: {{CONTENT_PILLARS}}

Aim for at least one usable candidate per pillar. Where a pillar cannot be filled with a source that survives the rules above, **leave it unfilled and say so** in the sourcing notes. An honest gap is a finding; a weak entry dressed up to fill a slot is a defect.

### Format for each candidate

```
## N. Headline-style title (how it could run in the issue)

**Category:** SHORT ALL-CAPS LABEL (e.g. FDA / PEPTIDES, MARKET, RETENTION)
**Source:** Outlet â€” "Article title"
**URL:** https://...
**Corroborating source:** (URL, or "none found")
**Date:** date of the event, and date of the article if different

**The Short Version:** One paragraph, plain and factual, of what happened.

**The Details:**
- 4-6 bullets of specifics. Numbers, dates, names, exact quoted language where it matters.
- Include the correction or caveat a reader is most likely to get wrong.

**Why It Matters:** One paragraph of what this changes for a {{NICHE}} operator. Analysis, not adjectives.

**Pillar:** which pillar this fills.
**Flag:** any sourcing weakness, staleness, sample-size problem, or unresolved discrepancy. Omit only if there genuinely is none.
```

### Required summary sections, after the candidates

**`## Recommended five`** â€” the five you would build the issue from. For each: the candidate number, its pillar, and one or two sentences on why it earns its slot. Then:
- A **pillar spread check** â€” name which pillar each of the five covers and confirm the spread is deliberate rather than accidental.
- A **named lead story** â€” "Lead with: #N" â€” and the reasoning. Timing, consequence, and counterintuitiveness beat everything else. If one candidate has a live deadline inside the delivery window, that is almost always the lead.
- **Strong alternates** if one of the five gets cut.

**`## Rejected sources and why`** â€” every source you looked at and threw out, grouped by reason, named by domain. Content-farm listicles, unattributed case-study economics, gated marketing dressed as research, paywalled or blocked outlets, stale items still surfacing in search results, and any figure whose attribution you traced and found broken. This section is not optional and is not a formality â€” it is how the editor knows what the floor was.

**`## Gaps and caveats for the editor`** â€” what the research could not establish, and what must not be published as a result. Write these as instructions ("Do not publish a CPM range from this research"), not as observations.

**`## Pillar coverage and sourcing notes`** â€” which pillars are filled and by what, which pillar is weakest and why, which items rest on secondary sources, and which are directly primary.

### Header the file with

Compiled date Â· audience Â· framing rule for the niche (any legal, medical, or claims constraint that governs what can be said) Â· a verification note stating that every URL was fetched and confirmed loading on a named date, and how blocked or paywalled sources were handled.

### Done means

10-12 candidates, every URL fetched, every secondary source flagged, every rejection named, a recommended five with a pillar spread and a named lead, and zero numbers you cannot point to a fetched page for.
