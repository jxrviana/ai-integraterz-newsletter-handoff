# Local Affiliate Pro — Issue 001: scrub bounced leads FIRST, then send via Bird

**Two jobs, in order:**
- **PART 1 (do first):** scrub every address that bounced/complained on our two prior campaigns out of our lists.
- **PART 2:** send **Local Affiliate Pro — Issue 001** (test → approval gate → ~19k) via **Bird**, to the cleaned list.

---

# PART 1 — Scrub bounced/complained addresses (do this before the send)

We do NOT want to hit dead or angry addresses again — it burns deliverability. Clean the lists first, then Part 2 sends to a clean master list automatically.

1. **Compile the bad-address list** from BOTH prior campaigns:
   - **The Dealmaker — Issue 1** (sent via **Resend**) — pull from the Resend dashboard/API for that send.
   - **The Referral Channel — Issue 1** — pull from whichever SMTP it was sent through. *(Xander also has a saved bounce file for this one locally if useful.)*
   - Include every **hard bounce**, **blocked**, and **spam complaint**; plus any address that **soft-bounced on both** sends (persistent).
   - **Combine + dedupe** into one master bad-address list.
2. **Clean the lists in ListMonk:**
   - Add every bad address to the **suppression / blocklist** (so no future campaign can hit them).
   - **Remove** them from the master **"All Leads Verified"** list AND from **every per-niche list**.
3. **Hand the file back to Xander:** export the final deduped bad-address list as a **CSV** and send it to Xander, so he can scrub his local source lead lists (master + per-niche) too.
4. **Report:** total unique bad addresses, how many were removed from each list, and the **final clean count** of the master list.

---

# PART 2 — Send Local Affiliate Pro, Issue 001

**Asset:** `local-affiliate-pro-issue-001.zip` (Xander will provide it) — contains `index.html` + `images/` (`hero.jpg`, `photo1.jpg`, `photo2.jpg`, `photo3.jpg`). This is a **finished, email-safe HTML build** — do NOT restructure, re-theme, or "improve" the layout. Your only edits are hosting the images + rewriting their `src` (below).

## Campaign settings
- **From:** `Local Affiliate Pro <local-affiliate-pro@send.usingaitoscale.com>`
- **Reply-To:** `xander@usingaitoscale.com`
- **Subject (single — NO A/B test):** `Main Street's unfair advantage`
  - We are **not** A/B testing this send — our open/click tracking isn't reliable yet, so a split would be measured blind. Send this one subject to the whole list.
- **Preheader:** already embedded as a hidden div at the top of the HTML — leave it as-is.

## Images — REQUIRED before any send
The HTML references images by **relative path** (`images/hero.jpg`, `images/photo1.jpg`, `photo2.jpg`, `photo3.jpg`). Email clients cannot load relative paths, so they MUST be hosted:
1. Upload all 4 images to the ESP media host.
2. Rewrite every image reference from the relative `images/…` path to the **hosted absolute URL**.
3. The **hero** is a **table-cell background image** with an **Outlook VML fallback** — update BOTH places: the CSS `background-image:url('images/hero.jpg')` AND the `<v:image … src="images/hero.jpg">` in the `<!--[if gte mso 9]>` block.
4. Confirm all 4 render in the test: the hero photo behind the "TAKE BACK MAIN STREET" headline, plus the 3 square photos beside the story beats.

## SMTP + send settings
- **Bird SMTP ONLY.** In ListMonk, make sure **Resend (and any other SMTP) is DISABLED** for this send so ListMonk cannot random-split the campaign across servers — **100% of this send goes through Bird.**
- **Rate:** **3–5 emails/sec, low concurrency** — the same safe pace as the Dealmaker send. Do not blast.
- **List:** the **cleaned master list from Part 1** (~19k, all prior bounces/complaints already removed).
- **Tracking:** open + click tracking MUST be ON and firing for this campaign (tracking pixel + link rewrite). **Verify it registers on the test** before the real send — this has failed silently before.

## STEP 1 — TEST (always first)
Send a test to all three:
- `justin@usingaitoscale.com`
- `xander@usingaitoscale.com`
- `xanderviana1@gmail.com`  *(to check real Gmail inbox placement)*

Then **report back**:
1. Did it arrive at each address? For the Gmail one — **Primary inbox, Promotions, or Spam?**
2. Do **all 4 images render**?
3. Does the CTA button go to `https://localaffiliatepro.com/agencies/`, and do **Unsubscribe** + **View online** work?
4. Did the test **register an open/click** in tracking?
5. *(Optional but recommended for a cold send:)* also send the test to a **mail-tester.com** address and report the score (aim 8+/10).

## ⛔ GATE — STOP HERE
**Do NOT send to the 19k until Xander explicitly approves after reviewing the test.** Silence or deflection is NOT approval. Wait for a clear "go."

## STEP 2 — real send (only after Xander's go)
Send to the **cleaned ~19k master list** via **Bird**, 3–5/sec, tracking on. Report final counts (sent / accepted / bounced) and opens/clicks once they come in.

---

## QA before the test (you own QA now)
- **Facts (no fabrication, ever):** the story cites **Jobber's affiliate program**. Verify it against the **live Jobber affiliate page in a real browser** (WebFetch false-404s on many sites — use the browser). The two anchored claims: the program invites people with *"an audience of field service business owners,"* and it markets an affiliate/referral program for that community. If the live page no longer supports the phrasing, **flag it — do not send.**
- **Links:** CTA → `localaffiliatepro.com/agencies/`; Unsubscribe + View-online = the ESP merge tags (`{{ UnsubscribeURL }}`, `{{ MessageURL }}`).
- **Render:** table-based, inline CSS, no external CSS/web-fonts, images hosted. Spot-check Gmail + Outlook + Apple Mail.
- **Footer:** physical address present (`37460 Beacon Brick Road, Zephyrhills, FL 33541`), no social links, and **no "AI Integraterz" anywhere** in the newsletter.
