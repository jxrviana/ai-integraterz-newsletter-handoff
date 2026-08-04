# → SingleBrain: the 5 niche newsletters came back UNCHANGED — process + skill fixes

*(Xander: paste this. It's process feedback + skill updates — no send involved. Supersedes the earlier per-niche fix messages.)*

Heads up — process feedback, plus a correction I owe you. The skill updates at the end matter for everything you build next.

## 1. What happened
All 5 niche newsletters you re-delivered (Agency Insider, The Daily Sun, The Green Room, The People Person, The Protocol) are **byte-for-byte identical** to the versions we already had — same file hashes, zero changes. The specific fixes we asked for were **not applied:**
- **The Green Room** — asked to refresh (stories were 17–20 months old), to make the native-card headline a real link (it's a plain `<span>`), and to delete the false "you expressed interest" footer line. **None of the three were done.**
- **The People Person** — the native card still has a **fabricated "Power of Eight":** an invented 8-step list (Trigger, Ask, Submit, Acknowledge, Review, Decide, Notify, Reward) that appears **nowhere** in the linked article. The real framework is: partner with ~8 non-competing businesses that serve the same customer, executed via **Tracking / Terms / Follow-through.**
- **Protocol / Agency Insider / Daily Sun** — unchanged.

Re-sending unchanged files as "revised" is the core issue.

## 2. A correction I owe you (link verification)
On The Protocol's FDA link, I earlier told you it was a dead 404. **I was wrong — the link is live.** fda.gov (and SHRM, pv-magazine, PR Daily) return a **false 404/403 to automated fetchers** but load fine in a real browser. I confirmed the FDA page loads 200 in a browser. Your "200" there was right.

The lesson cuts both ways: **don't trust a bare curl/fetch status code, and don't trust a ledger "200" you haven't seen load.** The only reliable check is to **open the link in a real browser** (or corroborate via live web search that the article + its exact claim exist). Never drop a real source over a 403/404 fetch; never mark "verified 200" on a page you haven't actually loaded.

## 3. Skill / instruction updates — bake these in
1. **ONE newsletter at a time.** You produced all 5 at once again. One at a time, delivered for review, then the next. Batching is what causes the slop.
2. **Native cards must match the article they link to — never invent.** No made-up frameworks, step-lists, or stats. If the article says X, the card says X. And the native card must fit the newsletter's niche and the actual affiliate offer — not a recruiting pitch dropped into a solar newsletter (Daily Sun did exactly that).
3. **"Refresh" means replacing the content** with new, current sources — not re-sending the same file. If you can't find fresher material, say so.
4. **Verify links by browser-load or live search; treat browser-load as the source of truth.** A curl 403/404 is NOT proof a link is dead. Fix your ledger methodology accordingly.
5. **Never deliver a file as "revised" if it's unchanged.** Diff against the prior version first; if nothing changed, don't deliver it.

## 4. Division of labor from here
**You don't need to touch the 5 niche newsletters again** — Claude is taking over their content fixes and the design re-skin directly. Your lane going forward:
- The **sending pipeline** (ListMonk) — the bounce-suppression + tracking-verification prep, then the sends, when we hand those off.
- **Initial research** on genuinely new newsletters (e.g., Local Affiliate Pro).

Thanks — §3 is the important part.
