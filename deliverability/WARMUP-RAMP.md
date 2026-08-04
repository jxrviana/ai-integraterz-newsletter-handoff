# Warm-Up Ramp — send.usingaitoscale.com (Resend)

The plan for delivering a large list (e.g. Local Affiliate Pro → the ~19k) from a **young domain** without getting flagged. The ramp IS the send — the ~19k goes out across the schedule, not in one blast.

## Why
`send.usingaitoscale.com` is ~1 week old with almost no sending history. A cold domain that blasts thousands on day one is how domains get blocklisted — regardless of perfect SPF/DKIM/DMARC. Ramping builds reputation as volume grows. (Justin approved this approach.)

## The schedule (~19k over ~12 days)
| Days | Volume / day | Running total |
|---|---|---|
| 1–2 | 250 | 500 |
| 3–4 | 500 | 1,500 |
| 5–6 | 1,000 | 3,500 |
| 7–8 | 1,750 | 7,000 |
| 9–10 | 2,750 | 12,500 |
| 11–12 | ~3,250 (remainder) | ~19,000 |

Adjust to the real list size. If Justin wants it faster, compress the later steps — never the early ones.

## Gate before EACH step-up (advance only if all true)
- Hard-bounce rate **< 2%**
- Spam-complaint rate **< 0.1%**
- Domain/IP **not** on any blocklist
- Opens holding steady (not collapsing)
- A seeded check-address in each batch still lands in the **inbox**

If any breaches: **hold** at the current level (repeat the day) or **drop back one level** and investigate before advancing. Never jump volume on bad metrics.

## How to send each batch
- **Cleanest contacts first:** send to the verified-deliverable segment before any catch-all/risky addresses (lowest bounce risk while reputation is thin).
- **Rate: 3–5 emails/sec, 1–2 connections** (the concurrency lesson — higher pushes 535s and looks spammy).
- **Suppress bounces** before each batch (bounces from earlier days → blocklist).
- **Resend-only** in ListMonk (Bird disabled) so nothing random-splits.
- Watch Resend's dashboard for any account warning — it's stricter than Bird on cold volume; if it flags, pause and reassess.

## Note
Content and auth are separate from reputation: LAP still needs its own mail-tester pass on the actual HTML before Day 1. Reputation is what this ramp buys.
