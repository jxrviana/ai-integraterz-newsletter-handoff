# AI Integraterz — Newsletter Pipeline

Working repository for the AI Integraterz / Using AI To Scale outbound-newsletter program. It holds the **context, docs, specs, and newsletter templates** so any device (Claude Code, etc.) can pick up the full picture.

> **Scope note:** lead lists and bounce lists (real email **PII**), image binaries, build zips, and any secrets are intentionally **excluded** from this repo via `.gitignore`. They live only on the working machine. This repo is **private**.

## Start here (read in this order)
1. **`CLAUDE.md`** — standing project context, rules, people/agents, the stack, the file map.
2. **`HANDOFF.md`** — current state; where everything stands right now.
3. **`BLOCKERS.md`** — known problems / open blockers.
4. **`NEWSLETTER-PLAYBOOK.md`** — the build spec (format, image rules, do/don'ts).
5. **`newsletters/00-SOURCE-OF-TRUTH.md`** — the newsletter strategy + model.

## What this program is
Outbound newsletters formatted as genuine trade publications. The CTA is the company's **affiliate-program** offer, appearing as exactly two mentions: one native story card at position 3 (styled identically to the news) + one house blurb. Flagships: **The Referral Channel** (editorial), **The Dealmaker** (direct), **Main Street Affiliate** (Beehiiv opt-in). Niche tier: **The Front Desk** (gyms), **Agency Insider**, **The Protocol**, **The Green Room**, **The People Person**, **The Daily Sun**.

## Folder map
- `newsletters/` — strategy + per-newsletter specs.
- `ready-to-send/` — finished newsletters (HTML + source). **`ready-to-send/the-front-desk/` is the LOCKED design template** — a 1:1 of The Rundown AI's layout (black masthead/section bars, neutral page, bronze accent). Every niche gets re-skinned into it.
- `_send-to-singlebrain/` — the briefs/messages handed to SingleBrain (the ESP/sending agent).
- `design-directions/`, `docs/`, `deliverability/` — supporting specs.
- Root `*-issue-001-revised.html` — SingleBrain-produced niche **content**, pending Claude re-skin into the Front Desk design.

## Who does what
- **Claude** — research architecture, QA + source verification, design/HTML, docs.
- **SingleBrain** — the ESP/sending agent (ListMonk + Bird); research + content generation.
- **Xander** — executes in the UIs, generates images, relays between Claude and SingleBrain.
- **Justin Bellware** — owner; owns DNS + the Bird account.

_Last updated: 2026-08-04._
