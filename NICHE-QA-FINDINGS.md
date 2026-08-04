# Niche Newsletter QA — Findings & Must-Fixes (2026-08-04)

QA of the 5 niche newsletters via 5 parallel Opus agents + real-browser verification.

**Key finding:** the "new newsletters" batch SingleBrain delivered was **byte-for-byte identical** to the existing root `*-issue-001-revised.html` files — no changes, requested fixes not applied. The `new newsletters/` folder was **deleted** (pure duplicate; verified all 10 files identical). The root `*-issue-001-revised.html` files are the current content base; the must-fixes below are for **Claude to apply during the design re-skin**.

## Systemic (all newsletters)
- **CTA domain `https://whimsy-nebula-47ch.here.now/`** resolves (to Justin's "I'm Your Money Guy" affiliate landing page) but is an ephemeral-looking preview host — and it's the ONLY CTA on every niche + the Front Desk + the Dealmaker. **ACTION: confirm with Justin it's permanent, or move to a stable branded URL before any niche send.** Tonal note: it's a personal direct-response pitch page — a jump from the editorial trade tone.
- **Link verification:** WebFetch/curl false-404/403 on fda.gov, SHRM, pv-magazine, PR Daily (bot-blocks). The FDA link previously flagged "dead" is actually LIVE. Verify via real browser load or live-search corroboration — never a bare curl status code.
- **Footer legal line:** CLAUDE.md says keep "Published by AI Integraterz" for CAN-SPAM; the Aug-1 build stripped all AII branding. Physical address IS present (satisfies CAN-SPAM). **DECISION NEEDED:** re-add the line or leave it off.

## Per-niche must-fixes
**Agency Insider** — sourcing strong + verified live (AdExchanger, Forrester, Accenture). Fixes: (1) Accenture/Whalar story ~8 wks old — reframe as analysis or swap; (2) soft claim "growing at nearly double the rate of US retail ecommerce" not on source — soften/source. Otherwise content-solid.

**The Daily Sun** (solar) — sourcing real + verified (First Solar; SEIA/Wood Mackenzie). Fixes: (1) **Card 2 headline says "First Half of 2026" but the data is Q1 2026** — body already says Q1; fix the headline; (2) **native card + Playbook are themed as "hiring/recruiting infrastructure" — wrong; rewrite to the affiliate offer in a solar frame.**

**The Green Room** (PR) — REFRESH NOT DONE. Fixes: (1) **stories 17–20 months old — replace with current (~≤60-day) PR stories** (needs fresh research); (2) **native-card headline is a `<span>` — make it a real `<a>`** to the Medium article; (3) **delete the false footer line** "you expressed interest in PR agency industry analysis"; (4) native card "Power of Eight" wording + "over 20% of new business" claim don't match the article — fix.

**The People Person** (recruiting) — SHRM sourcing solid + verified. Fixes: (1) **native card fabricates an 8-step "Power of Eight" (Trigger/Ask/Submit/Acknowledge/Review/Decide/Notify/Reward) — nonexistent in the article; rewrite to the real framework** (8 non-competing partners + Tracking/Terms/Follow-through); (2) $13.81B framing applies total US affiliate spend to recruiting — correct the context; (3) unsourced "California, Illinois, Massachusetts" copycat claim — source or generalize; (4) cards 1 + 4 ~1 yr old under "Latest Developments" — reframe.

**The Protocol** (men's-health coaching) — sourcing STRONG, all live (**FDA link IS live — do NOT touch;** PBS, Epic, Medium all real). Fixes: (1) **TOC item #2 + intro still reference a "TRAVERSE clinical-practice" card that no longer exists** (Card 2 is now the Pentagon/PBS screening story) — rewrite the TOC line + intro clause; (2) add the CAN-SPAM legal line if we keep it (see systemic).

## Go-forward
Claude fixes content + re-skins all 5 into the Front Desk (Rundown) design, using Xander's per-niche design inspirations. SingleBrain stands down on the 5 (process/skill feedback sent). The Green Room needs fresh PR research first.
