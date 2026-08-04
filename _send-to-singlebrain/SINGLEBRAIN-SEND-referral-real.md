# → SingleBrain: SEND The Referral Channel — REAL send via Bird

*(Xander: paste this + attach `ALL-LEADS-unified.csv`. This sends ONLY the Referral Channel. Leave The Dealmaker alone — it goes later.)*

Campaign **23 (The Referral Channel)** is loaded, tested, and approved. Send it for real now:

1. **Import** the attached `ALL-LEADS-unified.csv` (~19k; already includes the xander@ / justin@ seeds) as a ListMonk list.
2. **Assign campaign 23 (The Referral Channel)** to that list.
3. **Set the global SMTP to Bird** (you noted ListMonk's SMTP is global — the Referral Channel sends via **Bird**).
4. **Send campaign 23.**

**ONLY the Referral Channel.** Do **NOT** send campaign 24 (The Dealmaker) — that's a separate send later via Resend.

**Deliverability guardrails (important — this is a large send on a warming SMTP):**
- **Throttle / pace the send** if ListMonk or Bird supports it — do not fire all ~19k in one burst; a steady rate is much safer.
- If Bird's daily cap is below the full list, send what it allows and queue the rest for the next window.
- **Watch bounces + complaints live.** If bounces spike or Bird flags the send, **PAUSE immediately** and report — stopping early beats burning the SMTP.

Report back: total sent, delivered, bounced, complaints, and any errors.
