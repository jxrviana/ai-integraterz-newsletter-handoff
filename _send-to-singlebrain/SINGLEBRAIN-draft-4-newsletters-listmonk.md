# SingleBrain — Draft 4 newsletters in ListMonk (DRAFT ONLY — do NOT send)

We're staying on **ListMonk** for now (Sendy is on hold). Create these **4 campaigns as DRAFTS in ListMonk**. **Do NOT send, and do NOT test-send anything** — draft only. We'll trigger sends later, separately.

## For every one of the 4 (same process)
- Load the provided zip (`index.html` + `images/`).
- **Host all images** on the ESP and **rewrite every relative `images/…` src to the hosted URL** (including any CSS `background-image` and Outlook `<v:image>` fallback). Verify they render.
- **Format: Raw HTML.** Use the working template (the same one the prior sends used — a passthrough/minimal template, not one that double-wraps the HTML).
- Set From / Subject / Reply-To (below). **Reply-To for all = `xander@usingaitoscale.com`.**
- Assign the master list (**ALL-LEADS-unified**) for now — actual send list + volume is a separate warm-up step.
- Merge tags are ListMonk style: `{{ UnsubscribeURL }}` / `{{ MessageURL }}`.
- **Leave as DRAFT.**

## The 4

**1. The Dealmaker — Issue 2** · zip: `the-dealmaker-issue-2.zip`
- From: `The Dealmaker <dealmaker@send.usingaitoscale.com>` · Subject: **The local deal is not the offer**
- Images included: `banner.jpg`, `s1.jpg`. Byline Johana Buitrago.
- ⚠️ **Greeting merge tag:** the HTML opens with `Hi {{ FirstName }},`. Replace `{{ FirstName }}` with **ListMonk's real first-name merge tag AND a fallback** so it never renders "Hi ," (e.g. a `{{ if }}…{{ else }}there{{ end }}` form). Confirm the list actually carries first-name data.

**2. The Open Source — Issue 1** · zip: `the-open-source-issue-1.zip`
- From: `The Open Source <open-source@send.usingaitoscale.com>` · Subject: **Open-source AI for the businesses big tech forgot**
- Images included: `hero.jpg`, `logo.png`. CTA = `github.com/nousresearch/hermes-agent` (clean). Byline Theo Marsh.

**3. The Referral Channel — Issue 2** · zip: `the-referral-channel-issue-2.zip`
- From: `The Referral Channel <referral@send.usingaitoscale.com>` · Subject: **The affiliate link is becoming a newsroom beat**
- Images included: `lead.jpg`, `logo.png`. Byline Jay Bell.

**4. Local Affiliate Pro — Issue 1** · zip: `local-affiliate-pro-issue-001.zip`
- From: `Local Affiliate Pro <local-affiliate-pro@send.usingaitoscale.com>` · Subject: **Main Street's unfair advantage**
- Images included: `hero.jpg`, `photo1-3.jpg`. Byline Jordan Reyes.
- 🚫 **CTA WARNING — do NOT send this one:** its CTA points to `localaffiliatepro.com/agencies/`, which is currently **flagged by Google Safe Browsing**. Drafting is fine; **it must not be sent until the domain is cleared or the CTA is swapped to a clean URL** (Justin is handling).

## Cross-cutting flags
- **DRAFT ONLY. No sends. No test-sends.** (We send later once volume/warm-up + CTA links are sorted.)
- **CTA-link status (matters at send time, not now):** LAP → flagged (above). Dealmaker + Referral → `whimsy-nebula-47ch.here.now`, an ephemeral preview host — check it on Safe Browsing + mail-tester before any send. Open Source → clean.
- **Report back:** the 4 drafts created, image-hosting confirmed, the Dealmaker greeting tag set, and anything that needs Xander.
