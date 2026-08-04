# KNOWN BLOCKERS & OPEN ISSUES — Newsletter Pipeline

_Living list. Add issues as they surface; move to "Resolved" when fixed. Last updated: 2026-08-04._

## 🔴 Deliverability
- **Newsletter landing in Gmail SPAM (NEW — Aug 4).** The tracking-test email (real Referral Channel HTML, subject "The budget is quietly moving to partners") landed in Xander's Gmail **spam**, along with 3 bare Bird health-check / diagnostic emails. Earlier, during the main ~18.5k send, the newsletter reached the **primary inbox**. → Sender reputation on `send.usingaitoscale.com` likely dipped after the 18,565 warming-domain blast (bounces + zero engagement tracking + volume). Recoverable.
  - **Actions:** run a real inbox-placement test (mail-tester.com or multi-provider seeds — not a single self-address); warm gradually (small daily volume, most-engaged recipients first); verify SPF / DKIM / DMARC alignment on `send.usingaitoscale.com` (Justin owns DNS); keep bounces + complaints low; mark test emails "Not Spam." NOTE: bare health-check/diagnostic emails landing in spam is mostly noise (they look like test spam); the *real newsletter* in spam is the meaningful signal.
- **Bird warming domain shows "Throttled" + requires low concurrency.** Sending at >2 concurrent connections triggers 535 auth-style rejections; must send at 1–2 connections. Slows large sends.

## 🔴 Bird account / API (external — needs Bird-account access, likely Justin)
- **Bird API key lacks webhook scope** (`webhooks:read` / `webhooks:write`) → cannot wire the Bird → ListMonk bounce/complaint webhook.
- **Bird suppression/messages API pagination is broken** (malformed `...` cursor / HTTP 422) → cannot export unsubscribe or bounce lists via the API.
- **No authenticated Bird dashboard session for SingleBrain** → the Bird UI export path is also blocked.
- **Bird SMTP credential unstable** — repeated 535 "invalid/revoked key" during the main send; needed re-syncing. SMTP-send is a separate scope from the HTTP API key.
- **Durable fix:** one fully-scoped Bird API key (SMTP-send + webhooks) + a reliable export path (fixed pagination or an authenticated dashboard session).

## 🟠 Bounce / unsubscribe hygiene (blocked by the Bird items above)
- **Bounce webhook not wired.** ListMonk bounce processing is ENABLED (hard → blocklist, complaint → blocklist) but nothing feeds it — Bird webhook blocked (scope), no real bounce mailbox (only placeholder `pop.yoursite.com`).
- **43 Campaign-23 hard bounces not yet suppressed** (recipient-level export blocked).
- **Unsubscribe reconciliation OPEN (legal).** ListMonk shows 50 unsubscribed; Bird ~80; earlier 73. Up to ~30 possible unsubscribes not reconciled into ListMonk. **Must resolve before the next send.**

## 🟠 Tracking / analytics
- **Past send's opens/clicks permanently lost.** Campaign 23 (18,565 sent) went out with tracking OFF → no open/click data, unrecoverable.
- **Tracking now enabled** (`individual_tracking: true`) but **not verified end-to-end** — needs Xander to open + click a test (the test landed in spam; verify from there).

## 🟠 Data / exports (ListMonk + Bird API limits)
- **491 unsent recipients unidentifiable.** 19,056 audience − 18,565 sent = 491 that never delivered (535/EOF casualties). ListMonk API doesn't expose a per-recipient send ledger, so they can't be cleanly isolated for a targeted re-send.
- **Typed bounce CSV blocked** (Bird API pagination + no dashboard session).

## 🟡 SingleBrain reliability
- **Mis-certifies dead links as "HTTP 200 verified"** — twice logged 404 FDA URLs as 200. → Claude independently fetch-verifies every source link before acceptance.
- **Monitor/worker scripts crash mid-run** (SIGTERM) → historically paused sends prematurely.
- **Credentials appear in Slack logs** when it logs into ListMonk via browser (hygiene note).
- **Context/compression auth failures** → occasional mid-task context loss.

## ✅ Recently resolved
- Fabricated news sources (round 1) → re-sourced with real, fetch-verified publications (round 2, most verified).
- "Box / wrapper" render issue → ListMonk blank/raw template (ID 8).
- ListMonk open/click tracking → enabled (was off).
- ListMonk bounce processing → enabled (feed still pending, see above).
- Front Desk design → locked as the 1:1 Rundown template.
