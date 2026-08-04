# → SingleBrain: New Bird key in place — verify FIRST, then resume Campaign 23

The Bird API key was replaced (the old one was revoked -> 535 auth failure). Before resuming, VERIFY the new credential, then continue:

1. **Auth health-check (NOT the campaign):** send ONE test message through Bird to xander@usingaitoscale.com and confirm a clean 250 / accepted response — NOT a 535. Do not resume the campaign until this passes.
2. If the health-check passes, **resume campaign 23 (The Referral Channel, Bird)** at ~5 msg/sec (up to ~10 if Bird accepts cleanly; back off if it throttles).
3. **Wave 3: send up to ~10,000 total, then PAUSE and report** Bird's current totals (accepted, delivered, hard + out-of-band bounces, deferred, complaints) and the bounce rate. Do NOT auto-start the final wave — wait for the go.
4. **Auto-pause + report immediately** if the Bird bounce rate crosses ~3%, any complaints appear, Bird throttles, OR any auth/SMTP error recurs.
5. **Do NOT touch campaign 24 (The Dealmaker).**

If the auth health-check still returns 535, STOP — the new credential or the Bird account itself is still not right. Report it and we escalate on the Bird side rather than retrying.
