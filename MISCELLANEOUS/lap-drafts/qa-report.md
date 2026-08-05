# Local Affiliate Pro - Issue 001 QA report

**Status: DRAFT / NOT SEND-READY**

## A. Sourcing
- [x] One primary current angle selected: a live Shopify affiliate-program page opened in a real browser.
- [x] Official page title and final URL recorded in `source-ledger.md`.
- [x] Exact supporting evidence recorded for every Shopify claim used.
- [x] Main Street America community/networking source browser-verified and recorded.
- [x] No named fictional business presented as real.
- [x] HVAC owner passage explicitly labeled illustrative.
- [x] Unsupported commission rates, outcomes, approval claims, and relationship claims omitted.
- [ ] Freshness recheck before send: required because destination and program terms remain unresolved.

## B. Content and type
- [x] Continuous narrative, not cards, roundup, numbered offers, or TOC.
- [x] StoryBrand arc present: local-business hero -> advertising squeeze -> guide -> affiliate/community plan -> stakes -> one CTA.
- [x] Local business reader is the hero; Local Affiliate Pro is framed as guide.
- [x] Breaking-free theme is hopeful and practical, not conspiratorial.
- [x] Byline is Jordan Reyes.
- [x] CTA is singular and movement-framed: “See what your community and network are building.”

## C. Compliance
- [x] No `AI Integraterz`, `Published by AI Integraterz`, or `power partner` in customer-facing copy.
- [x] No banned terms: `game-changing`, `unlock`, `revolutionize`, `imagine if`, `supercharge`.
- [x] No fabricated named business, testimonial, commission, or performance result.
- [x] Illustrative image prompts and illustrative HVAC passage are labeled.
- [x] From and Reply-To are recorded in the source ledger and draft comment.
- [x] Physical address included.
- [x] `{{ UnsubscribeURL }}` and `{{ MessageURL }}` included.
- [ ] Destination/opt-in versus cold-outbound framing: unresolved blocker.
- [ ] CTA destination URL: unresolved blocker; HTML uses `href="#"` placeholder.

## D. Format and design
- [x] White background and wider max-width layout (820px).
- [x] Warm local palette, spacious structure, pull quotes, and image-as-format plan.
- [x] Inline CSS only; no `<style>` block.
- [x] HTML is email-safe baseline markup with table-free simple blocks and responsive viewport.
- [x] Image prompts are text-safe and clearly labeled for Xander.
- [ ] Generated image URLs/assets: pending Xander; HTML currently omits image references, so no broken-image risk.

## E. Delivery hygiene
- [x] Draft HTML saved at `/opt/data/local-affiliate-pro/issue-001/index.html`.
- [x] Image prompts saved at `/opt/data/local-affiliate-pro/issue-001/image-prompts.md`.
- [x] Source ledger saved at `/opt/data/local-affiliate-pro/issue-001/source-ledger.md`.
- [x] QA report saved at this path.
- [x] No ListMonk load, destination load, send, or test-send performed.
- [x] No old deals-roundup content retained in the rebuilt HTML.
- [ ] Final destination and CTA URL must be supplied before any platform load or send.

## Verification commands run
- HTML contains no `<style>` block.
- HTML contains required merge tags.
- HTML contains the required footer address.
- HTML contains no prohibited brand leakage or banned terms.
- Full automated checks are reported below.

## Blockers to resolve before send
1. Decide destination/platform and whether this is opt-in or cold outbound.
2. Replace `href="#"` with the approved CTA destination.
3. Re-check Shopify terms and all customer-facing claims at time of send.
4. Generate, host, and visually approve any images; preserve the no-text/no-logo constraints.
5. Run platform-specific preview and deliverability QA. Keep this issue draft-only until explicit approval.

**Conclusion:** Deliverables are complete as a review draft. It is intentionally not send-ready.

<!-- End QA report -->

## Automated check results
- See final tool output in the task transcript for the live checks against the saved HTML and companion files.
- This report remains a human QA artifact, not a claim that platform preview or delivery was tested.
