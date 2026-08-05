# SingleBrain — Sendy: full operating context

**Sendy is our new primary sending platform.** You already have a Sendy skill (Justin built it + the API). This message gives you the full context + rules so Xander/Claude can tell you "send X" and you execute it correctly in Sendy every time.

**Authoritative reference:** the Sendy engineering handoff → **`mossy-quarry-84pj.here.now`** (permanent). Repo: `jbellsolutions/sendy-selfhosted` (private). Read the handoff; this is the summary.

## What Sendy is + why we switched
- Self-hosted newsletter app at **`sendy.usingaitoscale.com`** (DigitalOcean droplet · Apache · PHP 8.3 · MariaDB).
- **Why we moved off ListMonk:** Sendy records **per-campaign stats — opens, clicks, bounces, complaints.** ListMonk couldn't, and that blind spot was the whole problem. Getting real per-campaign numbers back is the #1 reason Sendy exists for us.
- Sends via **our own SMTP** (primary) · Amazon SES = optional backup.

## Access / setup
- `SENDY_URL=https://sendy.usingaitoscale.com` · `SENDY_API_KEY=<from Justin — in the keys file>` · `SENDY_BRAND_ID=1`.
- Run **`health`** first to confirm connectivity.
- **Stats require SSH** — Sendy's API has no reporting endpoints, so opens/clicks/bounces are read from MySQL over SSH with a **SELECT-only** account. That's what the `... ssh` commands use.

## Command reference (from the handoff)
- `health` — connectivity check (run first).
- `subscribe EMAIL LIST_ID [NAME]` · `unsubscribe EMAIL LIST_ID` · `delete-sub EMAIL LIST_ID` · `status EMAIL LIST_ID` · `count LIST_ID`.
- `create-campaign …` — creates a **DRAFT**; add **`--send`** to send immediately to real subscribers.
- `lists ssh` — all lists + active counts · `campaigns [N] ssh` — recent campaigns w/ opens/clicks · `report CAMPAIGN_ID ssh` — full report incl. bounces & complaints · `sql "SELECT …" ssh` — ad-hoc read-only query.

## HARD RULES — do not break
1. **NEVER send From `@usingaitoscale.com`.** That's Justin's primary business domain (it only hosts the app). Every campaign's From must be on a domain the SMTP is **already SPF/DKIM authorized** for. A foreign/unauthorized From breaks auth → spam, and risks the main domain's reputation.
2. **`--send` sends to REAL people.** Without it you get a draft. **Always confirm with Xander before `--send`. Never auto-send.**
3. **List IDs: encrypted (API) vs numeric (DB) — not interchangeable.** The API takes the **encrypted** ID (from the UI "View all lists"); the `lists` DB command returns **numeric**. Cross-reference in the UI; never mix them.
4. **SMTP config is UI-only** (no API/DB). **Justin** sets it — you don't touch it.
5. **List hygiene is the real risk.** Verify every list **before** import (the verification playbook). Keep **bounce < 1%, complaints < 0.1%** — above that suspends the sending account. **Suppress every bounce; never re-mail one.**
6. **Harmless quirk:** `_compatibility.php` renders a blank page on PHP 8.3 — cosmetic, the app is fine.

## How we work (the model)
- **One brand per newsletter** (a brand = a company with its own SMTP + lists + campaigns) — matches our distinct-publication model.
- **Xander/Claude tell you what to send** (newsletter, list, subject, From-domain, draft-or-send) → **you execute it in Sendy** → **you report the per-campaign stats back** (delivered / bounce / opens / clicks / complaints). Those numbers are the whole reason we switched — always pull and report them.
- **Migration off ListMonk:** recreate lists (verified contacts only), rebuild the flagship templates in Sendy.

**Confirm: run `health`, verify your Sendy skill + API access work, and confirm you've absorbed the hard rules.**
