# GO — Send Local Affiliate Pro, Issue 001. Clear the blockers and send.

The newsletter is **approved and final**. No more QA, no more verification, no more research — that's done on our end. Your job is to **send it**. Below is exactly how to clear the three walls you hit, and the send rules. Do not come back with new gaps — resolve these and send.

## Your three blockers — resolved
1. **Jobber facts — VERIFIED, do not re-check.** Claude confirmed them in a live real browser. The Jobber affiliate page states verbatim: *"if you have an audience of field service business owners,"* *"Refer small business owners through your unique affiliate link and earn revenue,"* and *"industry-leading commission and no minimum sales requirements."* The claims are correct. **Ignore the old QA artifact that cites Shopify** — it's from a dead draft. The **only** source of truth is `index.html` in the ZIP.
2. **ListMonk session — reconnect, don't stop.** Re-authenticate with the **admin API credentials** (use the HTTP API, not a browser cookie that keeps expiring). A dropped session is a **reconnect, never a reason to halt.** If a call 401s, re-auth and continue.
3. **Resend 403 / Dealmaker bounces — not needed, skip.** We send via **Bird**, not Resend. Suppress the **530 Referral Channel bounces you already pulled** (`bird_bounced.csv`) so we don't hit them; Bird also auto-suppresses dead addresses on this send. **Do NOT run the full multi-list scrub or produce the suppression CSV now — it is not a send blocker.** Skip it. We'll do list hygiene separately later.

## Send config
- **From:** `Local Affiliate Pro <local-affiliate-pro@send.usingaitoscale.com>` · **Reply-To:** `xander@usingaitoscale.com`
- **Subject (single, no A/B):** `Main Street's unfair advantage`
- **Images:** host all 4 on the ESP and rewrite every relative `images/…` path to the hosted URL — including BOTH the hero's CSS `background-image` AND its Outlook `<v:image src=…>`.
- **SMTP:** **Bird ONLY.** Disable Resend/any other SMTP in ListMonk so it can't random-split — 100% via Bird.
- **Rate:** 3–5 emails/sec, low concurrency (same as the Dealmaker send).
- **List:** the ~19k master list, minus the 530 suppressed bounces.

## Sequence — test, then straight into the send
1. Send a **test** to `justin@usingaitoscale.com`, `xander@usingaitoscale.com`, `xanderviana1@gmail.com`.
2. If the images render and the links work, **proceed immediately to the full ~19k send** — Xander has pre-approved it, and he receives the test in his own inbox as the live check. **Do not wait for a separate approval.**
3. Only stop *before* the full send if the test is visibly broken (images missing / links dead). Otherwise, go.

## ⚠️ THE RULE: once sending starts, DO NOT STOP — except for a real safety breach
Run the send to completion. The **only** conditions that stop it:
- **Complaint rate ≥ 0.1%**, or
- a **hard-bounce spike** (well above normal), or
- the **sending IP/domain gets blacklisted**.

Nothing else stops the send. A stopped monitor, an expired session, a failed side-task, a tooling hiccup, a missing report — **none of these are stop conditions.** Reconnect and keep sending; report the issue afterward. This is exactly how the Dealmaker Issue 1 send was run. Do not self-pause.

## When done
Report: sent / accepted / bounced counts, plus opens/clicks if tracking captured them.
