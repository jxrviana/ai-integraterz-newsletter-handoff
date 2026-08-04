# → SingleBrain: Dealmaker — fix spam placement + prove click tracking BEFORE any send

*(Xander: paste this. Two blockers before the 19k. We agree with your hold — do not send the full list yet.)*

Good call holding. Two things to resolve: (1) the spam placement, (2) a valid click-tracking proof. Diagnose both, report, and we fix from there.

## 1. Deliverability — find the ROOT cause first
The test landed in spam. The most likely cause when you switch SMTPs is **domain authentication:** Resend needs its OWN SPF, DKIM, and return-path records on `send.usingaitoscale.com`. Bird's DKIM does not cover Resend. If Resend isn't fully verified for this domain, its mail is unauthenticated → spam.

- **Resend dashboard:** is `send.usingaitoscale.com` (and/or `usingaitoscale.com`) a VERIFIED domain in Resend, with DKIM, SPF, and return-path/MX all showing green? Report the exact status of each record.
- **Mail-Tester report** (the test already sent to `test-tlrykqdxv@srv1.mail-tester.com`): open the report on mail-tester.com and report: the score /10, and specifically the **SPF, DKIM, and DMARC results (pass / fail / aligned)**, any blocklist hits, and the content spam-score. That tells us whether this is an AUTH problem or a REPUTATION problem.
- **If Resend's DKIM/SPF are not set up for the domain** → that's the fix, and it requires **DNS records added at Hostinger (Justin's access)**. Pull the exact records Resend wants (from Resend's domain settings) and write them out cleanly so Justin can add them in one pass.

## 2. Fix the seed list + get a VALID click-tracking proof
Campaign 25 had **0 recipients** (the seed list saved with 0 subscribers) — that's why there was no proof, not a tracking failure.
- **Populate the seed list:** add real subscribers — `xander@usingaitoscale.com` + 1–2 you control. Confirm subscriber_count ≥ 2 BEFORE sending.
- **Real campaign send** (not the "test" button) to that seed list, over Resend.
- Xander opens it and clicks the CTA.
- **Confirm ListMonk records BOTH a new open AND a new click**, and report **inbox-vs-spam placement** in each seed mailbox.
- If a real send STILL shows 0 clicks, check that ListMonk is actually rewriting the body links with its tracking redirect (test-sends don't wrap links; a real send should).

## 3. THE GATE — do NOT send the 19k until ALL of these are true
- Mail-Tester: SPF + DKIM + DMARC all pass/align, score ≥ ~8/10.
- The seed send lands in the **INBOX**, not spam.
- ListMonk records the **open AND the click** on that seed send.
If any fail, fix it first.

## 4. Deliverability fixes (once we see the Mail-Tester result)
- **SPF/DKIM/DMARC alignment for Resend** (DNS via Justin) — top priority if auth is failing.
- **Warm gradually:** after auth is fixed, send small batches to the most-engaged/seed contacts first and ramp up — never 19k cold in one shot from a warming domain.
- **CTA link risk:** `whimsy-nebula-47ch.here.now` is an unknown/ephemeral domain — that can itself be a spam/link-reputation signal. Flag it in the Mail-Tester link analysis.
- **Copy:** The Dealmaker is a direct-response sales letter, which trips content filters harder than editorial. If Mail-Tester flags spammy phrases, note them and we'll soften.

**Report the Resend domain-auth status + the Mail-Tester breakdown. Hold the 19k until the gate in §3 passes.**
