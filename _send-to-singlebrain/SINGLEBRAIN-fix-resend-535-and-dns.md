# → SingleBrain: fix the Resend 535 + pull the exact DNS records for Justin

*(Xander: paste this. Two fixes — one you do now, one that produces a records list for Justin.)*

Good diagnosis. Two separate problems: an invalid Resend credential (nothing sends), and missing SPF/DMARC on the domain (why it goes to spam). Fix both.

## 1. Fix the Resend 535 (do this first — likely a blanked password)
`535 Authentication credentials invalid` = ListMonk's stored Resend SMTP password is wrong or empty. **ListMonk commonly blanks the SMTP password field when you edit + save a server** — so toggling Bird off / Resend on probably wiped the Resend key.

- In ListMonk's Resend SMTP settings, verify: host `smtp.resend.com`, port `465` (SSL) or `587` (TLS), **username literally `resend`**, and **re-enter the current valid Resend API key** (`re_…`, with sending permission) in the password field. Save.
- If the current key is actually invalid/revoked, **generate a fresh API key in the Resend dashboard** (API Keys → create, sending permission) and use that.
- **Do not paste the key in Slack.**
- Re-send one Mail-Tester test and confirm the **SMTP transport log shows a successful send (no 535)** — not just ListMonk's HTTP 200.

## 2. Pull the EXACT DNS records Justin must add (the spam root cause)
`send.usingaitoscale.com` is missing **SPF** and **DMARC** entirely, plus Resend's return-path/MX. That's why mail is unauthenticated → spam. From the **Resend dashboard → Domains → send.usingaitoscale.com → DNS records**, copy the EXACT records Resend requires and write them out as a clean list for Justin (he adds them at Hostinger):

Give me, as a copy-paste table of **Host / Type / Value**:
- the **SPF** TXT + the return-path/**MX** record Resend wants,
- the **DKIM** record(s) — confirm `resend._domainkey` matches what Resend shows,
- a **DMARC** TXT at `_dmarc.send.usingaitoscale.com` (at least `v=DMARC1; p=none; rua=mailto:…`).

Also report the domain's **verification status in Resend** (verified / pending / failed).

## 3. The gate stays
Do NOT send until BOTH: (a) the Resend key authenticates (no 535), AND (b) Justin adds the missing SPF/DMARC/return-path records and Resend shows the domain **verified**. Then: Mail-Tester score ≥ ~8/10 → seed-send open+click proof → staged send on Xander's go. Sending before the DNS is fixed just lands in spam.
