# Newsletter — Running Task List
**Updated 2026-08-05 (evening, post-huddle).** Source of truth: the Aug 5 huddle transcript + Justin's Sendy/verification handoffs + the `localaffiliatepro.com` flag incident. This overrides older priority lists.

## What changed today (the 5 shifts)
1. **Sendy is the new primary platform** (replaces ListMonk). It records **per-campaign stats** — opens/clicks/bounces — which ListMonk can't. That stat gap is the whole reason for the switch.
2. **Domain warming is now mandatory.** The flag happened because we blasted ~18.5k on a brand-new, unwarmed domain. Every new domain gets warmed; we buy + rotate domains continuously.
3. **List discipline:** bounce **< 1%**, complaints **< 0.1%**. Verify every list *before* sending.
4. **Lanes (Justin's own words):** **Xander = content (newsletters) + ops + recruiting + client management. Justin = deliverability + technical + domains/DNS.** Keep the heavy deliverability with Justin.
5. **Platform priority now: Sendy → SendFox (blocked on payment) → Velocity (least priority — don't touch).**

**Owner key:** 🟩 Xander/Claude do now · 🟦 Justin (nudge, then wait) · 🟨 joint

---

## ⛔ BLOCKED on Justin — nudge once, then don't spin on these
- **LAP send** — held until Justin clears the `localaffiliatepro.com` Safe Browsing flag (he said today). Then: swap CTA → re-test → send. 🟦
- **Standard CTA domain** — `whimsy-nebula-47ch.here.now` (on *every* newsletter) is the same risk class as the burned link. Justin stands up a stable branded CTA (`mainstreetaffiliate.com`); then Claude swaps it everywhere. 🟦→🟩
- **Sendy SMTP + API key** — Justin configures the SMTP (UI-only) + sends the API key. Sendy can't send until then. 🟦
- **Domain DNS auth** — SPF/DKIM/DMARC on any new domain = Justin. 🟦
- **SendFox payment** — Pro upgrade blocked; support emailed (Xander CC'd). 🟦

## 🟩 DO NOW — where our hours actually go (not blocked)

### A · Sendy set-up + migration (new primary)
1. Get the **Sendy API key** from Justin → install the skill (`SKILL.md` + `scripts/sendy.sh`) → run `health`.
2. Generate the SSH keypair, send Justin the `.pub` line → unlocks reading stats (opens/clicks/bounces) over SSH.
3. **Play with the Sendy UI** (Justin: "priority over Velocity") — brands, lists, campaigns, SMTP settings, reports.
4. **Brand structure decision** → recommend **one brand per newsletter** (matches the distinct-publication model; Justin leaned this way too).
5. **Migrate off ListMonk:** recreate lists, import **verified-only** contacts, rebuild the flagship templates in Sendy.

### B · Newsletter content — build the bank (Xander's core lane)
6. **Finalize design directions + templates** for the ones missing them: **The Open Source**, the **niches** (Front Desk ✅; Protocol, Green Room, People Person, Daily Sun, Agency Insider), **Main Street Affiliate**.
7. **Update existing:** Dealmaker **Issue 2** (Brian-Kurtz/Preeminence pivot — needs the Ultimate Swipe File from Justin), Referral **Issue 2** (new independent-news look).
8. **Build a bank of issues a week ahead** (Justin's ask) — start with **The Open Source**.

### C · Domains + warming — 🟦 Justin's lane (you only if he delegates)
Per the huddle, **domains + DNS + warming are Justin's.** You do **not** need Spaceship access unless he explicitly hands you domain-buying. If he ever does: buy cheap niche `.com`s on his Spaceship, tell him each one for DNS auth, start automated warmup — the how-to is in `docs/DOMAIN-WARMING-SOP.md` (kept as reference). Otherwise nothing to do here.

### D · Housekeeping
12. **SingleBrain update** message (drafted): Sendy migration, verification playbook, domain warming, bounce <1%, the CTA-domain lesson, never send From `@usingaitoscale.com`.
13. **Rotate the exposed Bird/Resend keys** (still outstanding).

## 🔁 ONGOING disciplines (every send)
- Verify the list first (bounce <1%, complaints <0.1%) · suppress all bounces (never re-mail).
- **Never send From `@usingaitoscale.com`** (Justin's primary domain — protect its reputation).
- Check every CTA/link domain on **Safe Browsing + mail-tester** before send (new QA gate).
- Always be warming new domains; hold a **consistent** daily volume (no spikes).

## 📌 SEPARATE TRACK (not newsletter — logged so it's not lost)
- Recruiting: VA for Chris Ward (job post → Reddit / Facebook / OnlineJobs / AI Integraterz group + email list); affiliate-manager JD (later). Client management / ops.

---

## ⏱️ How to spend the time (optimized)
Justin owns every blocker (LAP link, CTA domain, Sendy SMTP, DNS, SendFox payment). **Nudge him once, then don't wait.** Put your hours into **B — the content bank + templates**: it's un-blocked, it's your lane, and it feeds *every* platform. In parallel: do **A (Sendy)** the moment Justin sends the key, and **C (buy 1–2 domains + kick off warmup)** as a background task. **D** is quick. Don't touch Velocity.
