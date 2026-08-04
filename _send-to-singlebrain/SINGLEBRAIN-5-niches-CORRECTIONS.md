# → SingleBrain: REVISE all 5 niche newsletters — corrections required before they can move forward

Good work on the structure and writing — the format is right and the prose is strong. But the drafts **cannot proceed** because of one critical failure plus several fixable ones. Read this entire message and fix EVERY item. Do not assume anything; where a value is specified below, use exactly that value.

These are all CONTENT/FACT fixes. Keep your current layout — Claude still handles the final design. Put your effort into the facts.

---

## PART 1 — SOURCING (critical, non-negotiable): re-verify EVERY source by fetching it

This is the rule the whole product rests on: **no fabricated facts. Every statistic must trace to a real, live source that you actually fetched.** When I fetched your cited URLs, several returned **404 — the page does not exist.** That means the story and its stats cannot be trusted.

**Confirmed DEAD (404 — these URLs do not exist):**
- Agency Insider, Story 1 — `adage.com/article/digital-marketing-ad-tech/meta-and-googles-ai-can-create-ads-without-asking-how-guard-against-rogue-agents`
- The Daily Sun, Story 1 — `sltrib.com/news/2026/08/03/utah-produced-more-power-solar-than/`
- The Green Room, Story 4 — `prnewswire.com/news-releases/cision-unveils-inside-pr-2026-...-302078954.html` (the 62% / 23% / 8.3pt figures are unsupported — likely invented)
- The People Person, Story 2 — `forbes.com/sites/forbesstaffing/2026/08/02/americas-best-recruiting-temp-staffing-firms-2026/`

**Real source but WRONG numbers:**
- The Protocol, Story 4 — `epicresearch.org/...testosterone-prescribing-rates-rising-again` IS real, but it reports prescribing **prevalence rates** (0.83% in 2013 → 0.64% in 2021 → 0.95% in 2026), attributing the rebound to the FDA's **Feb 2025** removal of cardiovascular warnings (TRAVERSE trial). Your card's "7.4 million annually" and "40% below the 2014 peak" are NOT in that article. Fix the numbers to match the source, or cut them.
- The Protocol, Story 1 — your "July 2026 HHS/FDA label change" framing appears to conflate or replace the real Feb 2025 FDA change. Verify the exact event and date before keeping it.

**Could not confirm (verify these yourself by fetching):** The Protocol Story 2 (`cnbc.com/...military-plans-to-test-troops`), The Protocol Story 1 (`miamiherald.com/...`), The Daily Sun Story 2 (`seia.org/...`).

**What to do for ALL 15 news stories (3 per newsletter × 5), not just the ones above:**
1. **Actually fetch each source URL** (HTTP GET). Confirm it returns 200 (not 404/error) AND that the specific claim/number in the card appears in the page body.
2. If a URL is dead, or the stat is not on the page: either find the **correct real URL** for that exact story, or **replace the story** with a different, real, currently-verifiable one for that niche. 
3. **Do NOT invent statistics or paraphrase a number you cannot copy off a live page.** If you can't verify it, it does not ship.
4. **Deliverable — a VERIFIED SOURCE LEDGER per newsletter:** for each of the 3 news stories, give me: the final live URL, its HTTP status, and the **exact sentence or figure quoted from that page** that supports the card. That ledger is your proof.

The extraordinary claims especially (e.g. "the Pentagon will test every service member's testosterone") must be backed by a live, fetchable source or removed.

---

## PART 2 — Physical address (CAN-SPAM): three footers use a FAKE address

`Agency Insider`, `The Green Room`, and `The Protocol` footers currently read **"228 Park Ave S, PMB 90281, New York, NY 10003"** — that is not our address and is fabricated. Change all three to exactly:

**37460 Beacon Brick Road, Zephyrhills, Florida 33541**

(The Daily Sun and The People Person already have the correct address — leave them.)

---

## PART 3 — Bylines: one is duplicated, one is missing. Make all 5 unique personal names.

Use exactly these (personal name + "Editor, [Newsletter]"):
- **Agency Insider** → `Dana Whitfield` (currently "The Agency Insider desk" — replace with a real personal name)
- **The Daily Sun** → `Reed Calloway` (keep)
- **The Green Room** → `Camden Wells` (keep)
- **The People Person** → `Carson Greer` (keep)
- **The Protocol** → `Marcus Hale` (currently "Reed Calloway" — that duplicates The Daily Sun; change it)

Also update each rating link's `subject=` and any signoff to match its own newsletter.

---

## PART 4 — From / Reply-To (you set these wrong)

The sending domain is `send.usingaitoscale.com`. Set each newsletter's From address on that subdomain, and Reply-To to the monitored inbox. Update the review-draft comment block AND use these when loading into ListMonk:
- From: `[Newsletter] <agency-insider@send.usingaitoscale.com>` (and `the-daily-sun@`, `the-green-room@`, `the-people-person@`, `the-protocol@` on the same `send.usingaitoscale.com` subdomain)
- **Reply-To (all five): `xander@usingaitoscale.com`**

If any of those exact local parts is not authorized on `send.usingaitoscale.com`, tell me — do not silently substitute another domain.

---

## PART 5 — House blurb → CTA (fix the disconnect + standardize the CTA)

On four of them the "ABOUT [Newsletter]" blurb is an editorial mission statement, then an abrupt "Get the full playbook." The house blurb is the offer's second (and final) mention — it must bridge from the newsletter's identity into the offer in one or two soft sentences, then the CTA. Model it on The Front Desk:
> "This is [Newsletter]. We cover [what]. If your business has an offer that deserves a better acquisition channel, see how an affiliate program can fit around it."

- **Standardize the CTA text to:** `See the affiliate program →`
- **CTA link (all five):** `https://whimsy-nebula-47ch.here.now/`
- Keep it soft and editorial — no hard sell.

---

## PART 6 — Footer "why you're receiving this" line (currently false)

Lines like "you signed up at our landing page" / "you subscribed at our website" are untrue — these are cold outbound, not opt-in. Replace with a neutral, truthful line that does NOT claim they opted in, e.g.:
> "You're receiving this issue of [Newsletter] as a [industry] professional."

Keep the Read online + Unsubscribe links. Still NO sign-up link anywhere.

---

## PART 7 — Native card (position 3): match the REAL article + verify the link

The native card links to our Medium article, "Everyone Wants a Referral Channel. Almost Nobody Builds the Part That Makes It Real." Your card descriptions invent specifics (e.g. "generates over 20% of new business," "14 months"). **Re-read the actual article and describe it accurately.** The article's real content: most businesses never *operationalize* referral/affiliate programs; US affiliate spending is forecast near $13.81B in 2026; it presents the "Power of Eight" (partner with eight non-competing companies serving the same customers); the real barrier is execution, via three parts — **Tracking, Terms (pay roughly what a customer acquisition costs), and Follow-through (weekly management + timely payments).** Align each niche's native card to THAT, adapted to the audience. Do not invent article stats.

**Link:** verify `medium.com/p/f7d99f4f2f10` actually loads the correct article. Prefer that short form (it hides the author handle). If it does not resolve, use the full canonical URL.

---

## PART 8 — Minor render bug

`Agency Insider` (intro) and `The Green Room` (Story 1 details) contain `P&amp;amp;L` (double-encoded) — it renders as the literal "P&amp;L". Change to `P&amp;L` so it displays as "P&L".

---

## PROCESS — how to deliver

- **Fetch-and-confirm is mandatory** for every source. This gate is now permanent for all newsletters going forward.
- **Do Agency Insider FIRST — revise it fully + return its verified source ledger — then STOP for review.** Once I confirm your sourcing is now solid, revise the other four the same way.
- Deliver each as: the revised HTML + its verified source ledger (URL + status + exact supporting quote per story).
- **Do NOT send anything. Everything stays a draft.**
