# → SingleBrain: REAL stats for both sends — from the ESPs, not ListMonk

ListMonk's bounce/open/click counts are all showing 0, but that is because **no data feeds back into ListMonk** — not because the real numbers are 0. Two separate gaps:
- **Bounces / complaints:** ListMonk only shows these if the ESP posts them to its bounce webhook. That webhook is NOT wired, so ListMonk shows 0 bounces regardless of reality. **The real bounce data lives in the ESP dashboards.**
- **Opens / clicks:** these are ListMonk's own tracking (pixel + link redirect), and it's misconfigured — 0 recorded.

ListMonk's "sent" count (18,953 Dealmaker / 18,565 Referral) is only what it **handed to the ESP** — not what delivered.

## 1. Real delivery + bounce numbers — pull from the ESPs
- **The Dealmaker (Campaign 24, via RESEND):** from Resend (dashboard or API), for the send window Aug 4 ~21:20–22:56 — **delivered · bounced · complained · deferred/failed**, with rates.
- **The Referral Channel (via BIRD):** from Bird, for Aug 4 ~02:17–06:14 — **delivered · bounced · complained**, with rates.
Report the actual counts. If you can't reach a dashboard, say so and pull what you can from the API.

## 2. Wire the bounce sync (so we stop being blind)
Set up the **Resend → ListMonk bounce webhook** (Resend can POST delivered/bounced/complained events to ListMonk's bounce endpoint) so future sends record bounces and auto-blocklist hard bounces. Report whether you can configure it or what's blocking it. (Bird's webhook is still blocked on account scope — note if that's still the case.)

## 3. Fix opens/clicks tracking (separate issue)
0 opens/clicks a full day after the Referral send = a ListMonk tracking misconfig, not low engagement. Check: are body links rewritten through ListMonk's tracking redirect in sent messages? Is the open pixel present? Is the **root URL / tracking domain** set correctly? Report the root cause + fix so the next send records engagement.

## Report
The real ESP-side delivery/bounce numbers (§1) + the status of the two fixes (§2 bounce webhook, §3 tracking).
