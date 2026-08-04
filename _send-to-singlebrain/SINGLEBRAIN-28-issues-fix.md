# → SingleBrain: the 28 issues — full correction pass (image PROMPTS + Medium articles)

*(Xander: paste this whole message to SingleBrain. No attachments needed — it's reviewing the 28 HTML files it already has. This supersedes the earlier fix note.)*

---

Good work on the clean, email-safe skeleton across all 28 — no emoji, proper footers, the native-card-with-no-button discipline is right, and the Dealmaker letter format is correct. But they're **not sendable yet.** Below is the complete correction pass with everything you need. **Read all of it** — missing any piece is where mistakes come from.

---

## 1. CONTENT — the #1 fix (this is why they're not sendable)
Right now every story card reuses the **identical** "The Details" bullets across the whole issue ("Context: the source describes a market or operating change / Partner play… / Handoff… / Measure…"), the "Short Version" says nothing specific, and the sources are homepage/blog-index links (`healthandfitness.org`, `ihrsa.org/improve-your-club/`), not real articles. Some issues contain **zero specific facts or numbers.** That is exactly the "AI slop" Justin rejects, and it is not sendable.

**Every story must have:**
- A **real, specific article** as its source (a real URL to a real piece — never a homepage or a blog index).
- A **concrete fact or number** pulled from that article, stated plainly in the Short Version.
- **Unique** Details bullets written from that specific story — never the same bullets reused across cards.
- If a story has no specific, sourced fact, **cut it.** Fewer real stories beats more hollow ones.

**The two Dealmaker letters** are too vague ("research on referral value has examined whether referred customers behave differently" says nothing). Use the **concrete, cited stats** the original Dealmaker had: Alignable 85% (word-of-mouth is the #1 source), Nielsen 88% (trust in recommendations), Wharton/J. Marketing 16–25% higher LTV for referred customers, eMarketer affiliate-spend figures. Real numbers, real sources, every time.

---

## 2. BRAND NAMES — apply the right one per newsletter
All 24 niche issues currently say **"THE REFERRAL CHANNEL."** Each newsletter gets its **own** masthead, tagline, and footer brand:

| Newsletter | Type | Brand to apply |
|---|---|---|
| Editorial flagship | outbound | **The Referral Channel** |
| Direct-response flagship | outbound | **The Dealmaker** *(renamed from "The Rainmaker" — update everywhere; tagline "Turning relationships into revenue")* |
| PR agencies | niche | **The Green Room** |
| Solar | niche | **The Daily Sun** |
| Recruiting / staffing | niche | **The People Person** |
| Men's health (coaching + clinics) | niche | **The Protocol** |
| Marketing / AI agencies | niche | **Agency Insider** |
| Gyms | niche | **The Front Desk** |
| Tech / B2B | niche | **The Tech Stack** |

Also **rename the files** so we can tell them apart — e.g. `the-front-desk-issue-1.html`, not `index (12).html`.

---

## 3. STRUCTURE
- **Native / house card goes at position 3 (the MIDDLE) — never last.** Right now it's the final story, which blows its disguised-ad cover. Put it third in the run.
- **At least 4 news stories (5 preferred) + the native card.** Ten issues currently have only ~2 editorial stories — too thin.

---

## 4. IMAGES — you write the PROMPTS (you cannot generate images)
You don't have image generation, so **do not leave placeholder boxes and do not try to generate images.** Instead, for **every image slot in every issue**, write a **Higgsfield image PROMPT** that Xander will run himself to create the image.

- **One prompt per filename** (`banner.jpg`, `s1.jpg`, `s2.jpg`, …), clearly labeled by issue and slot, so Xander knows which prompt makes which image.
- **The banner is ONE prompt per newsletter**, reused across all issues of that newsletter (brand consistency) — not a new banner per issue.
- Keep the HTML referencing those exact filenames (`images/banner.jpg`, `images/s1.jpg`…) so the images drop straight in once generated.
- **Prompt standard — follow exactly (this is our hard-won image discipline):**
  - Photorealistic **editorial / press photography** — the kind that runs in a real news article. Specific, textured, natural light, lived-in. NEVER illustration, 3D, vector, stock-like, or sterile (that reads as AI slop and gets rejected).
  - **Text-safe:** choose scenes where **no surface could carry lettering** — no signs, screens, packaging, badges, book spines, vehicle livery, logos. ("No text" as a phrase is not enough; pick a framing with nothing to write on.)
  - **Vary** lighting, color, composition, and mood per slot — if two images look like the same shoot, change one.
  - The **native-card image (the house-ad slot) must blend in** with the story images — not cleaner, brighter, or more staged, or it flags the card as an ad.

---

## 5. MEDIUM ARTICLES — only for EDITORIAL newsletters, and ONE shared article
A Medium article exists only to be the believable "source" an **editorial** newsletter's native (disguised) "news" card links to via "Read more." So:
- **Direct-response newsletters (The Dealmaker) get NO Medium article.** Their CTA routes straight to the offer (`https://cal.com/usingaitoscale/aiintegraterz`) — no native-source card, no Medium.
- **Editorial newsletters (The Referral Channel + the niche newsletters) all point their native card to ONE SHARED Medium article** — a single general *"How AI Integraterz builds and runs your affiliate program"* explainer. **Do NOT write one per newsletter** (no 11 articles). The Referral Channel already has a published article — either reuse it as the shared one or write one clean shared piece.
- The shared article = **paste-ready HTML** + its **5 Medium tags** + **image PROMPTS** (same standard as §4).
- Once Xander publishes it, its live URL replaces `{{MEDIUM_URL}}` in every editorial issue.

---

## 6. BEEHIIV OPT-IN LINK — only on The Referral Channel (for now)
Add ONE small, low-key line — *"Get this free every week → Subscribe"* — pointing to the Beehiiv opt-in page (`aware-quarry-prs5.here.now`), in the footer or after the sign-off, **only on The Referral Channel.**
- **Do NOT add it to the niche newsletters** — a general-affiliate-newsletter plug is off-brand for a gym/solar/PR reader.
- **Do NOT add it to The Dealmaker** — keep that focused on the single CTA (book the call).
- Keep it secondary so it never competes with the main offer CTA. We'll test expanding it later.

---

## 7. SMALL FIXES
- `index (18).html` still has footer social links — remove them (no social links anywhere, per rule 25).
- Issue numbers are buggy ("No. e-2") — use clean "No. 002", "No. 003".
- Resolve `{{OFFER_URL}}` → `https://cal.com/usingaitoscale/aiintegraterz`.
- `{{MEDIUM_URL}}` → the newsletter's Medium article URL once it's published (placeholder until then).

---

## 8. UPDATE YOUR SKILLS / INSTRUCTIONS
Bake into your `newsletter-pipeline` (+ per-newsletter skills):
- 4+ news stories (5 preferred) + native card **at position 3**.
- Every story = a real article + a specific sourced fact; **no templated/reused bullets, no homepage links** — cut a story before shipping filler.
- **You write image PROMPTS, not images** (Xander generates them in Higgsfield).
- **One SHARED Medium article** for all editorial newsletters (not per-newsletter); **direct newsletters (The Dealmaker) get no Medium** — route straight to the offer.
- **Per-newsletter brand names** (table above) — never default everything to "The Referral Channel."
- **Beehiiv opt-in** = secondary link on The Referral Channel only.
*(These are playbook rules 25–30.)*

---

## 9. THE PROCESS — do ONE newsletter fully first, then scale (IMPORTANT)
Do **not** batch-produce all 28 + 11 Medium articles + ~180 prompts in one dump — that mass-production is exactly what produced the hollow first pass. Instead:
1. Pick **one** newsletter. Redo it fully: correct brand, real-researched issue(s), native card at position 3, 4+ real stories, its **image prompts** — and (if it's editorial) write the **one shared Medium article + its image prompts** (only needs writing once).
2. Deliver it as actual **`.html` files** (attach in Slack or email via `singlebrainslack@agentmail.to` — **not** pasted in chat). Xander generates the images in Higgsfield and we review the quality.
3. Once it passes the quality bar, scale to the rest the same way.

Then, every issue: run full QA (real-fact trace, card parity, native-at-3, link/placeholder check, spam scan, render), and do the internal **test send to `xander@usingaitoscale.com` + `justin@usingaitoscale.com` only. No list send** until we review.

---

## CONTEXT YOU NEED (so nothing is lost)
- **Offer** = the affiliate program (we build + run a business's affiliate program; partners sell on commission). **CTA** = book a call → `https://cal.com/usingaitoscale/aiintegraterz` (→ `mainstreetaffiliate.com` when live). **NEVER** say "power partner" in offer copy — say "affiliate program."
- **Byline** = Jay Bell on every issue. **From display-name** = the newsletter's own name. **Reply-To** = `xander@usingaitoscale.com`. **Seed every test send** with `xander@` + `justin@usingaitoscale.com`.
- **Footer** = the newsletter's own name + "Published by AI Integraterz" + `37460 Beacon Brick Road, Zephyrhills, Florida 33541` + unsubscribe. **No social links.**
- **Format** = editorial newsletters use six-ish cards (4–5 news + native at position 3); The Dealmaker is a direct-response letter (concrete cited stats, not news cards).
- No emoji anywhere. HTML entities for punctuation. Exactly one hidden preheader div. 600px tables, inline styles, ASCII-only.
