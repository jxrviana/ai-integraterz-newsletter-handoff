# General Skill — Sending (ListMonk + SMTP + deliverability)

> **⚠️ Updated Aug 5:** **SendFox is now an active sending channel** alongside ListMonk (easier / less-techy — use it to add volume). **SMTP + deliverability is Justin's lane** — Xander owns content; tell Justin what you need and he supplies credentials (SendGrid likely added later). Don't stress the infrastructure.

## ListMonk
- Engine on Railway. Load each newsletter as a **DRAFT**.
- Use the **BLANK/raw template (ID 8)** — our HTML is already a full email; the default template double-wraps it in a box.
- Host images via the **media API**.
- Merge tags: `{{ MessageURL }}` / `{{ UnsubscribeURL }}` (NO dot).
- Tracking: **`individual_tracking: true`** + open + click tracking ON (Justin requires full per-campaign stats).
- Bounce processing ON (hard bounce → blocklist; complaint → blocklist).

## SMTPs
- **Bird (#1)** and **Resend (#2)**, each ~50k/mo. **Always keep a 3rd warming** — SMTPs get shut down; that's normal, just make a new account.
- **ListMonk RANDOM-SPLITS across every ENABLED SMTP.** For a single-SMTP send, **DISABLE the others first**, or part of the send leaks out the wrong one.
- Per-newsletter SMTP: The Referral Channel = Bird; The Dealmaker = Resend.

## Send lessons (learned the hard way)
- **RATE: 3–5 emails/sec. CONCURRENCY: 1–2 connections.** A "535 auth failed" that keeps pausing the send is **CONCURRENCY, not a bad credential** — lower the connections; don't rotate keys.
- Don't pause the campaign if a monitor script dies — restart the monitor; ListMonk sends server-side.
- **Reconcile every address** at the end: sent + failed + bounced + suppressed = list total.

## Tracking proof
- **TEST sends do NOT reliably wrap links** → clicks won't register. Prove open + click on a **REAL send to a populated seed list (≥2 subscribers)**, not the test button.

## Deliverability
- **Each SMTP needs its OWN domain authentication.** Switching SMTP (e.g., Bird → Resend) requires adding that provider's SPF / DKIM / return-path records to DNS (Hostinger — Justin's access), or mail is unauthenticated → **spam**.
- Before any big send: run **Mail-Tester** (score ≥ ~8/10; SPF + DKIM + DMARC pass/align; no blocklist), and confirm a seed send lands in the **INBOX**.
- **Warm gradually** — small engaged batches first; never 19k cold from a warming domain.
- **Suppress bounces before each send** (Bird's webhook is blocked → do it manually).
- **Watch link reputation** — an unknown/ephemeral CTA domain can itself trip spam.
- Deliverability detail + live fixes: `DELIVERABILITY-FIX-PLAN.md`.
