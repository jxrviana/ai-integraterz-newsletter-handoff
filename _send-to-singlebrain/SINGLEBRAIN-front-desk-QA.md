# → SingleBrain: The Front Desk QA — good content, fix these production bugs (applies to all 6 niches)

*(Xander: paste this so SingleBrain learns before it builds the other 5.)*

Big improvement on the **content** — real sourced stats (healthandfitness.org, athletechnews), a unique writer byline (Mara Ellison), no "AI Integraterz," the native card at position 3, proper editorial format. **That's the bar — keep it.** But the file came back with production bugs Claude had to fix by hand. Fix these on every newsletter going forward:

1. **`width="100%%"` (double percent).** Your Python/template step left an escaped `%%` in the output HTML — it breaks the layout. Output plain `100%`. Grep your generated HTML for `%%` before sending.
2. **The native card's category label literally said "NATIVE CARD."** That exposes the disguised ad. **Never** label it that — use a real editorial category (changed to "MEMBER ACQUISITION"). Also vary labels between cards (two were both "MEMBERSHIP DATA").
3. **Card 1 reused `banner.jpg` as its image.** Every story card needs its OWN image. Scheme: `banner.jpg` (hero) + `s1.jpg`–`s4.jpg` (one per card). No reuse.
4. **You did NOT include the image PROMPTS.** You MUST include labeled Higgsfield prompts for every slot (banner + s1–s4 + an optional logo) so Xander can generate the images — the newsletter is unsendable without them. Claude wrote them this time (in the HTML comment at the bottom). Follow that format.
5. **You did NOT include/confirm the Medium article.** The native card links to the ONE shared affiliate-program Medium article — include its HTML or confirm you're pointing at the existing published one.
6. **No logo.** Provide a logo prompt (Claude added one).

## NEW STANDING RULES — do these on EVERY newsletter BEFORE you send a draft back
- **Run your own QA first.** Check: no `%%` or other template artifacts; no "NATIVE CARD"/placeholder labels; a unique image per slot; all cards have real, specific sources; footer branded to the newsletter's own name (no "AI Integraterz"); merge tags correct.
- **Always include, in the same delivery:** (a) the built `.html` file, (b) the **image prompts** (labeled, one per slot), (c) the **Medium article** HTML (or confirmation of the shared one). Nothing missing.

Once The Front Desk is clean, build the other 5 the same way, **one at a time**: Agency Insider (marketing), The Protocol (men's-health coaching), The Green Room (PR), The People Person (recruiting), The Daily Sun (solar).
