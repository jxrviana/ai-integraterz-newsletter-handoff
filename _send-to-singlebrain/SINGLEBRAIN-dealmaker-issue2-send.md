# → SingleBrain: The Dealmaker Issue 2 — CORRECTED re-send (new design + logo)

*(Xander: re-send this message + attach the UPDATED `the-dealmaker-issue-2.zip`. **Discard the previous version** — it had the wrong design.)*

---

The corrected Issue 2 is rebuilt in **The Dealmaker's real warm design** (ink / amber-gold / cream — not the Referral Channel dark/blue look you had before) and now carries the handshake **logo** in the masthead. The updated zip contains `index.html` + **4 images**: `banner.jpg`, `s1.jpg`, `s2.jpg`, `logo.png`.

Two things to resolve, then the test send:

**1. Image hosting — the blocker you hit.** ListMonk's media upload failed through your browser session. Use ListMonk's **media API** instead: `POST /api/media` (multipart form, authenticated with the apiuser + API token) to upload the 4 images, then point each `<img src>` at the returned hosted URL. If the API upload is also blocked, host the 4 images on the VPS / edcom server behind a public URL and reference those. **Report which path worked.** (Images must live at real public URLs — email clients won't load local paths, so this is required before any send.)

**2. Merge tags.** The file uses placeholder tags `{{VIEW_ONLINE_LINK}}` and `{{UNSUBSCRIBE_LINK}}`. Swap them for ListMonk's real tags — **`{{ MessageURL }}`** and **`{{ UnsubscribeURL }}`** — the same ones you correctly used on the previous version. A working unsubscribe link is required (CAN-SPAM).

Then set From display-name = **The Dealmaker**, Reply-To = `xander@usingaitoscale.com`, and run the internal **test send to `xander@usingaitoscale.com` + `justin@usingaitoscale.com` ONLY. No list send** — we review the real inbox first.
