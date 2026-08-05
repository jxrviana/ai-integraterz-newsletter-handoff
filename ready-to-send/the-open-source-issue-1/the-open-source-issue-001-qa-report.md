# The Open Source — Issue 1 QA Report

**Status: DRAFT BLOCKED pending editorial decisions and artwork.** No auto-send or test-send performed.

## A. Sourcing

- **Featured repository:** https://github.com/jbellsolutions/hermes-agent
- **Account page inspected in browser:** https://github.com/jbellsolutions
- **README inspected in browser:** https://github.com/jbellsolutions/hermes-agent/blob/main/README.md
- **Raw README inspected in browser:** https://raw.githubusercontent.com/jbellsolutions/hermes-agent/main/README.md
- **Package metadata inspected in browser:** https://raw.githubusercontent.com/jbellsolutions/hermes-agent/main/pyproject.toml
- **License page inspected in browser:** https://github.com/jbellsolutions/hermes-agent/blob/main/LICENSE
- **Browser result/date:** Specific public repository confirmed; README identifies the repository as `jbellsolutions/hermes-agent`, public, forked from `NousResearch/hermes-agent`. Inspected 2026-08-04 UTC.
- **Exact supporting claims captured:**
  - README: “The self-improving AI agent built by Nous Research.”
  - README: “It's the only agent with a built-in learning loop — it creates skills from experience, improves them during use, nudges itself to persist knowledge, searches its own past conversations, and builds a deepening model of who you are across sessions.”
  - README: “Lives where you do” and lists Telegram, Discord, Slack, WhatsApp, Signal, and CLI.
  - README: “Scheduled automations” and describes a built-in cron scheduler.
  - README: “Delegates and parallelizes” and describes isolated subagents and Python tool scripts via RPC.
  - README: “Runs anywhere, not just your laptop” and lists local, Docker, SSH, Singularity, Modal, Daytona, and Vercel Sandbox.
  - README: quick install via `curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash`.
  - `pyproject.toml`: version `0.12.0`, Python `>=3.11`, MIT license text, and project description about creating/improving skills and running anywhere.
  - Account README: currently indexing 199 repos, including 109 public, 90 private, and 2 archived. This was not used as a numerical claim in the email body because “199 projects later” is supplied as editorial direction and the repository page says “currently indexing 199 repos,” not “199 projects later.”
- **Non-fabrication note:** The body describes documented capabilities only. It does not claim Hermes is free of infrastructure/model costs. It does not claim a business result or specific installation outcome.
- **Duplicate check:** No prior The Open Source Issue 1 file was found in the local file search before drafting; this is a new newsletter issue.

## B. Content/type

- Editorial/informational feature, not a roundup and not a direct-response letter.
- Reader is consistently framed as the small-business hero.
- Builders are positioned as guides.
- Superhero identity is kept primarily in image direction and visual accents, not copy.
- Structure used: masthead, hero image, intro, thesis quote, problem, featured build, details, plain-English explanation, practical step, build-along tip, soft close, sign-off, footer.
- No cards, TOC, numbered offer list, affiliate offer, or bottom sales CTA.

## C. Compliance

- No `AI Integraterz`, `Published by AI Integraterz`, or `power partner` in customer-facing copy.
- No mandatory banned phrases: `game-changing`, `unlock`, `revolutionize`, `imagine if`, `supercharge`.
- No false relationship claims.
- Footer uses The Open Source and the required physical address.
- Uses `{{ MessageURL }}` and `{{ UnsubscribeURL }}` merge tags.
- **Open metadata blockers:** byline is still marked `[BYLINE PENDING CONFIRMATION]`; From address is not encoded in HTML and must be confirmed before platform setup.
- **Open link blocker:** direct link to `https://github.com/jbellsolutions` or the repository is intentionally withheld pending approval because the skill flags exposure of the shared operator handle. The current source note is plain text, not a clickable direct link.

## D. Format/design

- White background.
- Wider 760px max-width layout with mobile-friendly fluid width.
- Inline CSS only.
- Distinct palette: white, ink black, electric blue, comic red, restrained halftone reserved for artwork.
- Text-safe image alt text included.
- Hero image is a pending placeholder and must be replaced by approved Xander artwork before any approved test.
- No external fonts, scripts, forms, or CSS files.
- Images are not yet rendered or visually parity-checked because artwork has not been generated.

## E. Delivery hygiene

- Draft HTML saved at `/opt/data/newsletter-review-packages/html/the-open-source-issue-001-draft.html`.
- Image prompts saved at `/opt/data/newsletter-review-packages/prompts/the-open-source-issue-001-image-prompts.txt`.
- This report saved at `/opt/data/newsletter-review-packages/qa/the-open-source-issue-001-qa-report.md`.
- No auto-send performed.
- No test-send performed.
- No SMTP action performed.

## Open decisions requiring approval

1. **Byline:** confirm `Theo Marsh` or provide replacement.
2. **From address:** confirm `open-source@send.usingaitoscale.com` or choose another approved local-part such as `builders@` or `hq@`.
3. **Repository/account link:** approve or reject a direct link to `https://github.com/jbellsolutions` / the featured repository, acknowledging that it exposes the shared operator handle.
4. **Free-tool destination:** approve a destination before adding a download/use CTA. The current draft does not promise a live download link.
5. **Artwork:** replace `IMAGE_HERO_URL_PENDING` after Xander supplies approved image URLs. Optional in-story visuals are not inserted yet.
6. **Identity lock:** confirm the current palette and `&#9889;` masthead emoji, or replace before final rendering.

## Final gate

Do not mark complete until the decisions above are resolved, artwork is inserted, HTML is rendered in a browser, desktop/mobile appearance is checked, links and merge tags are validated, and the approved draft-only/test-send policy is explicitly followed.

## Deliverables

- Draft HTML: `/opt/data/newsletter-review-packages/html/the-open-source-issue-001-draft.html`
- Image prompts: `/opt/data/newsletter-review-packages/prompts/the-open-source-issue-001-image-prompts.txt`
- QA report: this file

