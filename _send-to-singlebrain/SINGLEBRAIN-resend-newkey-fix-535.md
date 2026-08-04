# → SingleBrain: fix the Resend 535 with the new key, then a VALID seed test (auth is already verified)

*(Xander: replace the placeholder with your new Resend API key before pasting. After SingleBrain enters it, delete this message from Slack so the key isn't left in the logs.)*

**Correction to the earlier DNS finding:** the Resend domain `send.usingaitoscale.com` IS **verified** — SPF + DKIM are live and confirmed in Resend's own dashboard. The reason your direct query for SPF/MX on `send.usingaitoscale.com` came back empty is that Resend places those on the **`send.send`** return-path subdomain (standard). So **auth is NOT the blocker** — disregard "SPF missing / needs Justin." The blockers are only: the 535 (bad stored key) and the fact that the domain is brand-new (a reputation/warming issue, not a config one).

**Verified in Resend (reference — do NOT change these):**
- DKIM TXT `resend._domainkey.send` → verified
- SPF MX `send.send` → feedback-smtp.…amazonses.com → verified
- SPF TXT `send.send` → v=spf1 include:…amazonses.com ~all → verified
- (DMARC at `_dmarc.send.usingaitoscale.com` is the only record not present — Xander is adding it at GoDaddy separately. Not your task.)

## 1. Fix the 535 (new key)
New Resend API key:
```
<<PASTE_NEW_RESEND_API_KEY_HERE>>
```
- ListMonk → Settings → SMTP → the Resend server: username `resend`, host `smtp.resend.com`, port `465` (SSL) or `587` (TLS), paste the key into the **password** field, **Save**. (ListMonk blanks the password on edit — confirm it's actually filled before saving.)
- Resend enabled, Bird disabled.

## 2. Populate the seed list, then a REAL seed send (proves transport + tracking + placement at once)
- Add real subscribers to the seed list: `xander@usingaitoscale.com` + 1–2 you control. **Confirm subscriber_count ≥ 2** (Campaign 25 failed because the list had 0).
- Send **The Dealmaker Issue 1** to that seed list as a **REAL campaign** (not the "test" button), over Resend.
- Confirm and report: (a) no 535 in the transport log, (b) it arrives, (c) Xander opens + clicks → ListMonk records **BOTH the open AND the click**, (d) **inbox-vs-spam placement** in each seed mailbox.
- Also send one to Mail-Tester (`test-…@srv1.mail-tester.com`) and report the **score + SPF/DKIM/DMARC results + any content/link flags** (e.g., the CTA link domain).

## 3. Report — do NOT do the 19k
Report all of §2. We decide the send strategy from there — and it will be a **WARMING ramp (small → larger over days)**, not a 19k blast from a 7-day-old domain. Sending big now just teaches Gmail this domain is spam.

## Security
After you enter the key, tell Xander so he can delete it from the Slack message.
