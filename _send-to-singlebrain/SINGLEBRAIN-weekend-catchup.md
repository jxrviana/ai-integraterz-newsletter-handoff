# → SingleBrain: Weekend catch-up — new tools, updated stack, current to-dos

*(Xander: paste this to SingleBrain to get it aligned on everything Justin built over the weekend. It may already know some of this from Slack — this makes sure.)*

---

Quick alignment on everything that changed over the weekend, so we're on the same page for the newsletters.

**The 3 affiliate newsletters (unchanged):**
- **Main Street Affiliate** — the OPT-IN flagship on **Beehiiv** (people subscribe; Justin-content-heavy).
- **The Dealmaker** — outbound, direct-response (JV / power-partner angle).
- **The Referral Channel** — outbound, editorial.

**New tools / systems now live:**
1. **Beehiiv** (Main Street Affiliate's home). Opt-in page is live. You have the `beehiiv` skill (API v2 — subscribe, lists, posts, segments). ⚠️ The Beehiiv API key returned 401 on the last test — confirm it's active (or get a fresh one from Justin), and get the Publication ID, before relying on it.
2. **Our own SMTP server — edcom / "Partner Power Mail"** (`esp.partnerpowermail.com`, domain `partnerpowermail.com`). A standalone ESP we own; you have the `spaceship-smtp` skill. Auth is green (SPF/DKIM/DMARC). ⚠️ It's a COLD IP — Gmail already flagged a test as spam. Do NOT blast cold lists through it; warm it on engaged contacts. Use it as the **gray-hat tier-2 SMTP** (for riskier addresses).
3. **Email verification API** (`verify.partnerpowermail.com`). Verify a list BEFORE importing: `/verify`, `/verify/batch`, `/progress`, `/credits`. ~9.5k/day cap. Returns deliverable / catch-all / risky / dead.
4. **SendFox** — Justin purchased it; another sending platform in the mix.

**New rule — match the sender to the list tier:**
- **DELIVERABLE** (verified-live) contacts → **premium tier-1 SMTP** (Bird / Resend).
- **SENDABLE** (catch-all / risky) contacts → **gray-hat tier-2** (our own edcom server).
- **Always verify a list before importing/sending.** Protect sender reputation — never blast unverified or dead addresses.

**New leads:** the **Agency Owners** list (marketing / AI agencies, with some PR + staffing mixed in): `deliverable_contacts_first10k.csv` (~4.4k confirmed-live) + `sendable_contacts_first10k.csv` (~8.2k sendable-with-care). ⚠️ Categories aren't clean — needs a domain/website check before it's used for a niche newsletter. The sendable file overlaps the deliverable one — segment by the `verify_verdict` column, don't double-send.

**New content:** the **Kurtz 5-day welcome series** (`kurtz-list-mindset-5day-series.md`) = the **welcome sequence for the Beehiiv flagship (Main Street Affiliate)**. When Main Street is built on Beehiiv, set this up as the welcome automation (Day 5 still needs a CTA).

**Current newsletter to-do (priority order):**
1. Finish the **Referral Channel Issue #2** pilot — you generate the images yourself, and **deliver the HTML as an actual file** (attach/email), not chat text; then QA + test send to xander@ + justin@ only.
2. **Build Main Street Affiliate on Beehiiv** (opt-in flagship) — now unblocked; wire up the Kurtz welcome series.
3. Keep **verifying + tiering** every list before send (deliverable→premium, sendable→gray).
4. **Warm the edcom own-server** on engaged contacts before any real volume.

Hard rules unchanged: nothing sends to a list without Xander + Justin approval; verified stats only; no "power partner" in offer copy; footer = the newsletter's own name, no social links.

Heads-up: that recurring "401 … title generation … key invalid" error — keep an eye on it and flag if it ever blocks a real step.
