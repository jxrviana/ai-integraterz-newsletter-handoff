# Email Platforms & Technical Handoff — for Justin

**Purpose:** everything you need to take over the email/sending side — every platform we use or send from, the technical state, what's happened so far, and the open items to build a full system. Prepared 2026-08-06.

> **Start here, then read `HANDOFF.md` (current project state) and `skills/` (the build system).** Nothing has *sent* from the 4 new newsletters yet — they're drafts, gated on a clean CTA domain (see §6).

---

## 1. The active sending stack (what actually ships mail today)
- **ListMonk** = the campaign manager we send from. Open-source, self-hosted on **Railway** (`listmonk-production-2930.up.railway.app`). It builds the campaign, holds the lists, and hands each message to an SMTP server.
- **SMTP (the transport) = Bird + Resend.** ListMonk is configured with both; they do the actual mail transmission. Both authorized on the sending domain **`send.usingaitoscale.com`**.
- Everything else below is backup / on-hold / future.

## 2. Full platform inventory

| Platform | Role | Status | Sends from / host | Key notes |
|---|---|---|---|---|
| **ListMonk** | Campaign manager | **ACTIVE** | Railway (`listmonk-production-2930.up.railway.app`) → SMTP | Merge tags `{{ UnsubscribeURL }}` / `{{ MessageURL }}`. **Open/click tracking is broken**; **doesn't record bounces without a webhook**; the SMTP **password field blanks on edit** (re-enter it or you get a 535); it random-splits across *enabled* SMTPs (disable the others for a single-lane send). |
| **Bird** | SMTP #1 | **ACTIVE** (verified, warming) | `send.usingaitoscale.com` · IP `192.174.87.116` | $15 Startup ≈ 50k/mo. IP has a good Mailspike reputation. (Shows as "SparkPost" inside the Velocity UI.) |
| **Resend** | SMTP #2 | **ACTIVE** | `send.usingaitoscale.com` | $20 transactional ≈ 50k/mo. Had a 535 auth error caused by ListMonk blanking the key on edit. |
| **Sendy** | Self-hosted ESP | **ON HOLD** | DigitalOcean `68.183.152.141` · `sendy.usingaitoscale.com` | $69 one-time. **Records per-campaign stats (opens/clicks/bounces)** — the exact thing ListMonk can't. Paused because it's a heavier learning curve right now; strong candidate when we want real stats. Stats read from MySQL over SSH (no reporting API). |
| **Velocity MTA / edcom** | Self-hosted ESP + own MTA | **ON HOLD** (least priority) | Spaceship VM · `esp.partnerpowermail.com` · sending IP `104.207.90.88` (verify-hub `104.207.90.227`) | EmailDelivery.com's edcom-ce + Velocity MTA — sends from **our own dedicated IP**, no third-party ESP. This is the long-term *owned-infrastructure* play (can't get shut down like rented ESPs). Currently a **cold IP on a 50/day warm-up ramp** and wants engaged traffic, so it's not a cold-blast tool yet. Includes a **verify-hub** (`verify.partnerpowermail.com`) that grades lists deliverable/catch-all/risky/undeliverable. You built it; the full runbook is the `edcom-operate` / "grassy-lotus" skill. |
| **SendFox** | Creator ESP | **BLOCKED** (payment/upgrade) | — | AppSumo lifetime. **Opt-in only — its TOS bans cold/purchased lists.** Right for the opt-in flagship, not cold outbound. |
| **Beehiiv** | Opt-in flagship platform | **FUTURE** | opt-in page `aware-quarry-prs5.here.now` | For **Main Street Affiliate** (genuine subscribers). Not set up yet. |
| **JangoMail** | Legacy ESP | Side-test | `scaleverticalwithai.com` | ~5k cap, resets monthly. Old sends had no click tracking. |

## 3. Sending domain + authentication
- **Sending domain: `send.usingaitoscale.com`** (a subdomain of your primary `usingaitoscale.com`). **Rule we hold: never send From the bare `@usingaitoscale.com`** — keep the primary domain's reputation untouched by bulk mail.
- **Auth is clean:** SPF ✓, DKIM ✓ (valid + aligned), and the Bird IP has good reputation — all confirmed on mail-tester. So *how* we send is healthy.
- **DNS lives at Hostinger** (Xander has no access; you do). Some domains are on **Spaceship**.

## 4. Tracking & stats — the known gap
- **ListMonk open/click tracking is broken** (pixel + link-rewrite not firing). We have deliverability numbers but **no engagement data**.
- **ListMonk doesn't record bounces** without an ESP→ListMonk webhook — bounce/complaint counts are pulled **manually from the Bird/Resend dashboards**.
- Per-campaign stats method today: filter the ESP dashboard by From + subject + date (ListMonk shows account-wide, not per-campaign).
- **This is the main reason Sendy is on the table** — it records per-campaign opens/clicks/bounces natively.

## 5. What's been sent (the real numbers)
- **The Dealmaker — Issue 1** (via Resend): **19,097 sent · 98.74% delivered · 240 bounced (1.26%) · 3 complaints (0.02%)**.
- **The Referral Channel — Issue 1** (via Bird): **18,556 sent · 98.17% delivered · 340 bounced (1.83%) · 0 complaints**.
- Opens/clicks: **not tracked** (see §4). Both sends were healthy on deliverability + complaints.

## 6. The deliverability lesson (most important thing to know)
- **Local Affiliate Pro's test landed in spam — because of the CTA *link*, not the domain.** The link `localaffiliatepro.com` is **Google Safe-Browsing-flagged AND in Razor2** (a collaborative spam database, confirmed on mail-tester). Auth, IP, and sending domain were all clean. **A flagged link spam-folders the entire email regardless of how well you send.**
- **Current CTA-link status:**
  - **LAP → `localaffiliatepro.com`** = flagged. **Do not send until cleared.**
  - **Dealmaker + Referral → `whimsy-nebula-47ch.here.now`** = an ephemeral preview host, same risk class — **verify on Safe Browsing + mail-tester before any send.**
  - **Open Source → `github.com/nousresearch/hermes-agent`** = clean.
- **New standing rule:** before ANY send, check every CTA/link domain on Google Safe Browsing + run the campaign through mail-tester.
- **What we need from you here:**
  1. **Clear the Safe Browsing flag** on `localaffiliatepro.com` (Google Search Console → Security Issues → Request Review).
  2. **Stand up a stable, branded CTA domain** (e.g. `mainstreetaffiliate.com`) to replace the flagged/ephemeral links across the affiliate newsletters.
  3. **Move ListMonk's links/images/unsubscribe off the `railway.app` subdomain** onto a real custom domain (a `*.up.railway.app` host in every link is a secondary spam signal).
  4. **Per-brand mailing addresses** (real P.O. boxes / virtual mailboxes) so footers don't share one fingerprint — currently all use `37460 Beacon Brick Road`.

## 7. Warm-up & list hygiene
- The domain is **not cold** (already sent ~37k with good auth/IP) — so the gate isn't warm-up, it's **clean CTA links + list hygiene.**
- Targets: **bounce <1%, complaints <0.1%.** Verify every list before sending; suppress all bounces.
- Planned ramp on ListMonk: start ~**250/newsletter/day** (Open Source first — it has the clean CTA), hold consistent, ramp ~30–50%/week. **Domain-warming how-to:** `docs/DOMAIN-WARMING-SOP.md`.

## 8. The newsletters (ready, gated on §6)
Four are finalized in `ready-to-send/` — each its own distinct design so no two read as one sender: **The Dealmaker #2** (cream-paper editorial), **The Open Source #1** (clean, credits Nous Research), **The Referral Channel #2** (its own dark newsroom look), **Local Affiliate Pro #1** (magazine template). All are **draft-ready in ListMonk**; none should send until the CTA domain is clean.

## 9. Security / housekeeping
- **Rotate any keys that passed through chat/Slack:** Bird, Resend, Sendy, edcom.
- **Not in this repo, by design:** the `Sendy Keys.txt` file, all lead CSVs (PII), and meeting transcripts are gitignored. Secrets should reach you through your own secure channel, never the repo.

## 10. Where everything lives in the repo
- `HANDOFF.md` — current project state (read after this).
- `skills/` — the full newsletter build system: `general/` (pipeline, creation+QA, format, offer, design, images, **`06-sending-listmonk.md`**, swipe-file) + `newsletters/` (one per title).
- `ready-to-send/` — the 4 finalized newsletters (HTML + prompts + QA).
- `docs/` — `DOMAIN-WARMING-SOP.md` + specs. `deliverability/` — deliverability fix notes.
- `RUNNING-TASKS.md` — the live task list. `_send-to-singlebrain/` + `messages/` — the operational handoff messages.

## 11. Open technical items for you to own
- [ ] Clear the LAP Safe Browsing flag + stand up a branded CTA domain (§6).
- [ ] Fix ListMonk open/click tracking + wire a Bird/Resend → ListMonk bounce webhook (§4).
- [ ] Decide the platform path: keep ListMonk, or move to **Sendy** (real stats) / **Velocity** (owned IP) — and if Velocity, run the IP warm-up.
- [ ] Move ListMonk links/images/unsubscribe onto a custom domain (§6).
- [ ] Per-brand sending domains + mailing addresses.
- [ ] Rotate the exposed keys (§9).
