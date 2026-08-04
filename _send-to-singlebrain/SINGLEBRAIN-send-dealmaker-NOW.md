# → SingleBrain: SEND The Dealmaker — Day 1 of the ramp, NOW

**Xander has approved the send. Here is the exact, unblocked path. Stop gating and start Day 1.**

## What was actually wrong
- The attached ZIP's HTML used the wrong unsubscribe tag (`{{UNSUBSCRIBE_LINK}}`) and relative image paths — correct call not to load it as-is.
- BUT **Campaign 24 is already ListMonk-ready**: it's the tested version whose seed (Campaign 27) landed in Xander's inbox, with images already hosted. Use it.

## Do this — fastest legal send
1. **Check Campaign 24's body for `{{ UnsubscribeURL }}`.**
   - Present → the campaign is legal and ready (images already hosted). Go to step 2.
   - If Campaign 24 also has `{{UNSUBSCRIBE_LINK}}` or a broken/empty unsubscribe → do one find-replace to `{{ UnsubscribeURL }}` in the campaign body and save. Now it's legal.
2. Confirm: **Resend enabled, Bird disabled**, and yesterday's bounces suppressed.
3. **START Day 1 of the warm-up ramp: send to 250 of the cleanest / verified-deliverable addresses** on the ~19k master list. Rate **3–5/sec, 1–2 connections**. **This is authorized — Xander approved the ramp start. Do NOT wait for further sign-off on Day 1.**
4. Report: sent count, bounces, any errors, and a spot-check of whether a seeded address landed in inbox.

## Tracking — do NOT block the send on this
The seed's open/click didn't register. Investigate in parallel (confirm ListMonk is rewriting the body links with its tracking redirect), but do NOT hold Day 1 for it — losing stats on 250 emails is acceptable, and we fix it before the larger batches.

## If Xander requires the LATEST copy instead of Campaign 24
Claude already corrected the latest HTML's unsubscribe tag (`{{ UnsubscribeURL }}` + a `{{ MessageURL }}` view-online link). For images, **reuse the hosted image URLs already in Campaign 24's body** — copy them out and swap the relative `images/…` paths for them (no new upload needed). Then load and send Day 1 as above.

**Bottom line: get Day 1 (250) out the door now. Campaign 24 is the ready path.**
