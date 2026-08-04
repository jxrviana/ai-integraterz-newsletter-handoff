# → SingleBrain: The Referral Channel — release Wave 2 (bigger + faster)

Wave 1 looks clean: 1,000 sent, 0 bounces, 0 complaints, no Bird or ListMonk errors. Good — let's scale up the volume and the rate.

Resume **campaign 23 (The Referral Channel) on Bird** and send the next wave:

1. **Volume:** send ~4,000 more, then **auto-pause at 5,000 total** sent.
2. **Faster pacing:** step the rate up to roughly **5 messages/second** — increase concurrent connections and/or batch size as needed to hit that. This is a deliberate ramp up from Wave 1's ~1/sec.
3. **Safety auto-pause (keep this):** stop immediately and report if you see ANY bounce, complaint/spam report, rejection, rate-limit warning, or SMTP error. If Bird flags throttling or a rate limit, **back the rate down — do not push through it.**
4. **Do NOT touch campaign 24 (The Dealmaker).** Referral only.

Report back: total sent, delivered (if ListMonk exposes it), bounces, complaints, and any Bird acceptance or rate-limit warnings.

If Wave 2 is as clean as Wave 1, we'll release the remaining ~14k in one or two larger waves right after this.
