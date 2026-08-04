# → SingleBrain: Bird SMTP credential diagnostic — NO campaign sending

Do not resume Campaign 23. Bounce rate is healthy (1.487%, 0 complaints) — deliverability is fine. The only blocker is the Bird SMTP login returning 535 even though the Bird HTTP API accepts the key. Pin down the exact cause — no campaign mail, just isolate the credential:

1. **Confirm the split.** Run the Bird HTTP API health check AND a Bird SMTP auth test (each just one message to xander@usingaitoscale.com, our own seed). Report both. If HTTP returns 202 while SMTP returns 535, the SMTP credential is the problem — and it is a SEPARATE credential from the HTTP API key.
2. **Report ListMonk's current Bird SMTP settings:** host, port, and whether a username and a password value are set (do NOT paste the secret — just confirm presence).
3. **Report what Bird requires for SMTP relay:** does Bird issue dedicated SMTP credentials (username + password) distinct from the HTTP API key? What exact host / port / username does Bird's SMTP expect?
4. **Report any Bird account suspension, security alert, or abuse/volume flag.**

Goal: know whether the fix is "put Bird's correct SMTP username/password into ListMonk" (a config fix -> we finish tonight) or "Bird flagged the account" (need a different SMTP). No sending until we decide.
