# SingleBrain — updated direction (Aug 5 huddle). Get aligned with these.

The newsletter operation changed today. Here's what's now true, so your skills + actions match it.

## 1. Sendy is the new PRIMARY platform (migrating off ListMonk)
- **Why:** Sendy records **per-campaign stats — opens, clicks, bounces** — which ListMonk cannot. That was the deal-breaker.
- Live at `sendy.usingaitoscale.com`. You already have a **Sendy skill** (Justin built it + the API). Use it.
- Stats are read from **MySQL over SSH** (Sendy's API has no reporting endpoints) — the `report` / `campaigns ssh` commands.
- **Priority order: Sendy → SendFox → Velocity.** SendFox is **blocked on a payment issue** (don't rely on it yet). **Velocity/edcom = least priority, do not touch** (Justin still updating it).

## 2. Verification before every send — all platforms (Justin's directive)
- Update/keep the verification playbook (`grassy-lotus` / edcom verify-hub) so it runs **for every list on every platform** — not just one. Full funnel (syntax → MX → disposable → gateway → Microsoft inbox check → SMTP), keep only **DELIVERABLE** for cold sends.
- **Target: bounce < 1%, complaints < 0.1%.** No list touches a sending tool until it's been verified.
- **Suppress every bounce** — never re-mail a bounced/complained address on any tool.

## 3. Domain warming is mandatory now
- The `localaffiliatepro.com` link got flagged because we blasted ~18.5k on a **brand-new, unwarmed domain**. Never do that again.
- **Every new domain gets warmed** (start small, ramp gradually, hold **consistent** daily volume — no spikes). Warmed domains carry the load; new ones warm in the background. We buy + rotate domains continuously (some will burn — expected).
- **Never send From `@usingaitoscale.com`** — that's Justin's primary business domain; sending from it would risk its reputation. Use only authorized sending domains.

## 4. Link/domain reputation is now a hard pre-send gate
- **Check every CTA/link domain on Google Safe Browsing + run mail-tester before any send.** A flagged link = the whole email goes to spam (that's what happened to LAP).
- The standard CTA `whimsy-nebula-47ch.here.now` is an ephemeral host and a risk — flag it; we're moving to a stable branded CTA.

## 5. Local Affiliate Pro is HELD
- Built correctly, but held until Justin clears the `localaffiliatepro.com` flag or gives a clean CTA URL. Do not attempt to send it. Xander is running it manually once unblocked.

**Confirm you've absorbed these and updated the relevant skills (Sendy, verification, warming).**
