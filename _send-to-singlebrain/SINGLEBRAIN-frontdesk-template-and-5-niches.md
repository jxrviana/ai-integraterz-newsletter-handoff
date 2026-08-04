# → SingleBrain (NEW THREAD): The Front Desk template + build the 5 remaining niche newsletters

Attached: **the-front-desk.zip** (index.html + images/s1-s4.jpg). This is the finished, approved Front Desk newsletter. It is the **locked template** for every gym / Front Desk issue, and the build standard for all niche newsletters. Read this whole message before acting.

---

## PART A - Load the Front Desk as a DRAFT (do NOT send)

1. Unzip. Upload the 4 images (`images/s1.jpg`-`s4.jpg`) to ListMonk media (same media API you used for campaign 23), and replace each `images/sN.jpg` src in the HTML with its hosted ListMonk URL.
2. Create a NEW ListMonk campaign as a **DRAFT**:
   - **Subject:** `The market's fuller than ever. Is your front desk ready?`
   - **From name:** `The Front Desk`
   - **From email:** `frontdesk@send.usingaitoscale.com` (or the closest authorized local part on `send.usingaitoscale.com` - tell me if that exact address isn't authorized)
   - **Reply-To:** `xander@usingaitoscale.com` (required - the From domain is send-only, so replies must route here)
   - **Template:** the blank/raw template (ID 8). The HTML is a complete email - do NOT double-wrap it.
   - Merge tags are already in the HTML: `{{ MessageURL }}` and `{{ UnsubscribeURL }}` (no leading dot).
3. **Leave it as a DRAFT. Do NOT send.** Xander reviews the ListMonk preview and approves before anything sends.
4. Save this design + structure as the reference template for all future Front Desk issues.

---

## PART B - The build standard (replicate this EXACTLY for every niche)

### Research (the most important rule - no fabricated facts)
- Every story is a **real, current, verifiable** news item with a **real, live source URL**.
- **Every statistic must trace to that source.** If a number can't be verified on a live page, it does not go in. (Front Desk used healthandfitness.org and athletechnews.com - all stats verified live.)
- **4 story cards per issue: 3 real news stories + 1 native card at position 3.**

### The native card (always position 3)
- Styled **byte-identical** to the news cards. It must look like a normal story - NEVER labeled "sponsored," "native," or "ad."
- Category label = a real editorial category for the niche (Front Desk used `MEMBER ACQUISITION`).
- Headline + "Read more" link -> the shared affiliate-program Medium article: `https://medium.com/@ai_integraterz/everyone-wants-a-referral-channel-almost-nobody-builds-the-part-that-makes-it-real-f7d99f4f2f10` (use this for every niche for now; Claude finalizes the exact per-niche link in the design pass).
- "Why It Matters" ties the story to how an affiliate program helps that niche - soft, never a pitch.

### Structure (each issue, in this order)
1. Hidden preheader (one teasing line).
2. **Masthead:** the newsletter's OWN name + one-line tagline + `ISSUE 00X - MONTH YEAR`.
3. **Intro card:** "Good morning, [audience]." + 2-3 framing sentences (a point of view) + "In today's rundown:" + a bulleted contents list.
4. Section bar: `LATEST DEVELOPMENTS`.
5. **Story cards 1-4** (card 3 = native). Each: CATEGORY label -> emoji + headline (links to source) -> image -> "Image source: [publisher]" -> **The Short Version:** (1-2 sentences) / **The Details:** (4 bullets) / **Why It Matters:** (1-2 sentences) -> "Read more ->".
6. Section bar: `THE PLAYBOOK`.
7. **Utility card** `ONE USEFUL MOVE`: a free, specific, actionable tip for that niche.
8. **House blurb:** "This is [Newsletter]. ..." + one soft offer line + CTA "See the affiliate program ->" linking to `https://whimsy-nebula-47ch.here.now/`
9. **Sign-off card:** "That's it for this week." + a reply-inviting line + "How useful was this issue?" + 3 star-rating buttons (`mailto:xander@usingaitoscale.com?subject=[Newsletter] feedback: Nailed it / Average / Needs work`) + "See you next week," + a UNIQUE writer byline + the newsletter name.
10. **Footer** (dark block): the newsletter's own name + "Published by [Newsletter] - (c) 2026" + physical address `37460 Beacon Brick Road, Zephyrhills, Florida 33541` + "Read online" (`{{ MessageURL }}`) + "Update preferences or unsubscribe" (`{{ UnsubscribeURL }}`).

### Hard rules
- **Offer mentioned EXACTLY twice:** the native card (position 3) + the house blurb. Nowhere else.
- **Unique writer byline per newsletter** (Front Desk = Mara Ellison). Invent a plausible one per niche.
- **NEVER write "AI Integraterz"** anywhere. The brand is the newsletter's own name.
- **Banned words:** game-changing, unlock, revolutionize, imagine if, supercharge. Also never "book a call" or "power partner."
- **CTA link (niches):** `https://whimsy-nebula-47ch.here.now/`. **NO sign-up / opt-in link** anywhere (that opt-in is only for the Beehiiv flagship, not the niches).
- **NO social links in the footer.**
- **Merge tags:** `{{ MessageURL }}` and `{{ UnsubscribeURL }}` - no leading dot.
- **Include IMAGE PROMPTS for every image slot.** Xander generates the images. Label each (s1-s4), photorealistic editorial/documentary, and **TEXT-FREE** - no words, letters, logos, screens, or signage in the frame.
- **Subject line:** a curiosity/benefit hook off the lead story. Propose one per niche.
- **From:** `[Newsletter]` <localpart@send.usingaitoscale.com>; **Reply-To:** `xander@usingaitoscale.com`.

### Self-QA before delivering each (check ALL)
- No template artifacts - grep the output for `%%` and for any `{{ }}` that isn't the two merge tags.
- No placeholder labels ("NATIVE CARD", "sponsored", lorem, etc.).
- A UNIQUE image prompt per slot (no reuse).
- Every card has a real, specific, LIVE source.
- Footer branded to the newsletter's own name; address + unsubscribe present; no socials; no sign-up.
- Offer mentioned exactly twice. No banned words. No "AI Integraterz."

---

## PART C - Build the 5 remaining niche newsletters

Build these five, **ONE AT A TIME** (full research + self-QA on each before the next):

1. **Agency Insider** - marketing + AI agencies
2. **The Protocol** - men's health (coaching + clinics)
3. **The Green Room** - PR agencies
4. **The People Person** - recruiting / staffing
5. **The Daily Sun** - solar

For EACH niche, deliver:
- The newsletter following PART B.
- The labeled, text-free image prompts (one per slot).
- The full **source list** - every stat with its live URL.
- A proposed **subject line** + a unique **writer byline**.

### CHECKPOINT (important)
**Build `Agency Insider` FIRST, then STOP and report it for review** before starting the other four. Once Xander confirms it meets the standard, continue with the remaining four, one at a time. This way any misunderstanding costs one newsletter, not five.

### IMPORTANT on design
Do **NOT** worry about matching the Front Desk's exact visual design. Use whatever layout/template you already have - **Claude will re-skin each niche into the locked Front Desk design and send you the final HTML/zip to load.** So put your effort into **research + content quality + the hard rules above** - that is the part that can't be fixed in the design pass.

**Do NOT send anything. Everything is a draft for review.** Report each niche as you finish it.
