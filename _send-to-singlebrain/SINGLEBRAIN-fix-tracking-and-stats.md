# → SingleBrain: fix per-campaign stat tracking (opens/clicks + Resend bounce sync)

The ESP delivery numbers are healthy (Dealmaker ~98.9% delivered / 1.1% bounce / 0.01% complaints via Resend; Referral ~98.3% / 1.69% bounce / 0 complaints via Bird). The gap is **per-campaign tracking**. Two fixes + an interim method.

## 1. Fix ListMonk's open/click tracking (it should work per-campaign, natively)
Both campaigns show 0 views / 0 clicks — an instrumentation bug, not zero engagement. Debug it:
- Send a fresh SMALL **real** campaign to `xander@usingaitoscale.com` (not the test button). Xander opens it and clicks a link.
- **Inspect the RECEIVED email's raw source:**
  - (a) Is ListMonk's tracking **pixel** present — an `<img>` pointing at `…/campaign/…/px.png`?
  - (b) Are the body **links rewritten** through `…/link/…`?
  - **If MISSING** → the blank/raw template (ID 8) or the campaign settings are stripping tracking. Fix so the pixel + link-rewrite are in the sent message (use a template that preserves ListMonk tracking, and confirm link-tracking is enabled on the campaign).
  - **If PRESENT but the counters stay 0** → the tracking endpoint at the root URL (`listmonk-production-2930.up.railway.app`) isn't recording. Test it directly: does the `px.png` load, and does a `/link/…` URL redirect? If the Railway app is unreachable/sleeping for those endpoints, fix that.
- Report the root cause + fix. Once fixed, ListMonk shows opens/clicks **per campaign** automatically.

## 2. Wire Resend → ListMonk bounce sync (per-campaign bounces, automatic)
Resend can POST delivered/bounced/complained events to a webhook. Set up a **Resend webhook** pointing at ListMonk's bounce endpoint so bounces auto-sync per campaign and hard bounces auto-blocklist. (Xander has Resend dashboard access to add the webhook — coordinate the endpoint URL with him.) Report the endpoint + status. Bird's webhook stays blocked on scope — park it.

## Interim per-campaign stat method (use until the above is live)
Do NOT use manual baseline-diff. Instead: **filter the Resend dashboard by the campaign's From address + subject + send-date window** — that isolates one campaign's delivered/bounced/complained directly (each campaign has a unique subject). For Bird sends, use the account summary over the send's date window (we send one campaign at a time, so it isolates cleanly).

Report §1 findings + fix and §2 webhook status.
