# → SingleBrain: Referral Channel Issue #2 — QA feedback + generate images + build the HTML as a FILE

*(Xander: paste the message below to SingleBrain. SingleBrain owns the WHOLE pipeline end-to-end now, images included.)*

---

Great pilot run — the research and copy came out strong, and you nailed the native-card discipline, the honesty labels on the vendor stats, the utility segment, and image briefs that even respect the "native image must blend in" rule. A few QA fixes, then generate the images and build an actual file.

**Fix in the copy:**
1. **Strip the research artifacts.** Link-preview / citation cards leaked into the body — the "Awin / [link] / Jan 29th | Added by Single Brain V2…" and "impact.com / … / Est. reading time" blocks are sitting inside Story 1's and Story 4's "The Details" bullets and in the image-brief table. Those are research/unfurl artifacts, NOT newsletter content. The final copy and HTML must contain only the actual story text — remove every one.
2. **Source diversity (note for this and future issues).** All three editorial stories come from affiliate-industry vendors (Awin, Impact.com ×2). You labeled the vendor claims honestly, which is right — but for an *editorial* newsletter we want at least one independent/journalistic source, and the eMarketer "$1 in $7 of ecommerce" figure should be verified at eMarketer directly rather than second-hand through Awin. For THIS pilot issue, keep the three stories but (a) strip the artifacts and (b) soften any claim you can't trace to a primary source.
3. **Resolve the offer link.** `{{OFFER_URL}}` in the house-blurb button → `https://cal.com/usingaitoscale/aiintegraterz`. Leave `{{MEDIUM_URL}}` on the native card as a placeholder for now — Issue #2's Medium article comes after the HTML, and we'll wire the live URL in then.
4. **Match Issue #1's identity exactly.** Use The Referral Channel's established masthead, tagline, and palette from the Issue #1 example you have — don't introduce a new tagline.

**Generate the images yourself — this is your step, end-to-end.** Produce all 6 images (banner + s1–s5) from the briefs you already wrote, using your own image generation. Hold them to this quality bar:
- Photorealistic editorial / press photography — the kind that runs in a real news article. NOT sterile, minimal, stock-like, or obviously AI (that gets rejected as "slop").
- **Text-safe:** no readable text or logos anywhere in frame (a "no text" instruction isn't enough — pick framings where no surface could carry lettering).
- A **different look per image** — vary lighting, colour, composition. If two look like the same shoot, redo one.
- The **native image (s3) must blend in** with the other story photos — not cleaner, brighter, or more staged, or it flags the card as an ad.
- **Look at each finished image** and regenerate any with stray lettering — don't trust a self-report.

If you genuinely have **no** image-generation capability, stop and tell us clearly — we'll add an image-generation tool to you rather than route this to Claude. Also **update your `newsletter-pipeline` skill** so image generation is *your* step: the earlier version pointed images to "Claude/Higgsfield" — that's changed, you own the full pipeline end-to-end.

**Deliver the output as actual FILES, not chat text.**
- Build the email-safe HTML with your images, matching Issue #1's design/palette, and **deliver it as a real `.html` file** — attach it in Slack, or email it to Xander from your AgentMail inbox (`singlebrainslack@agentmail.to`). Do NOT paste the HTML in chat; Xander needs a file he can open and view.
- Same for the Medium article — deliver it as a paste-ready `.html` file (+ its 5 tags).

Then run full QA (stat-trace, card-parity check, link + placeholder check, spam-word scan, render check) and do the internal **test send to `xander@usingaitoscale.com` + `justin@usingaitoscale.com` ONLY**. No list send — we review the files and the test first.

Thanks on the 401 check — sounds like a stale title-helper key rather than your DeepSeek key. Keep an eye out and flag it if it recurs mid-pipeline.
