# SingleBrain — update your newsletter skills to CURRENT (Aug 6)

This is the authoritative state of every newsletter + the general rules. **Update your per-newsletter skills AND your general newsletter skills to match this.** Then, at the very end, **list back every newsletter-related skill you have** so we can confirm you digested all of it. *(Source of truth if you have repo access: `github.com/jxrviana/ai-integraterz-newsletter`, the `skills/` folder — otherwise this message is authoritative.)*

## Platform (current)
**ListMonk is the sending platform.** Justin's call: Sendy is too complex for now — **Sendy + Velocity are on hold.** Merge tags: `{{ UnsubscribeURL }}` / `{{ MessageURL }}`. **Never auto-send — draft only; Xander approves every send.**

## The 4 finalized flagships (each is its OWN publication — a reader who gets two must never guess one sender)

**1. The Dealmaker** — *editorial/informational; Brian Kurtz + Jay Abraham "preeminence."*
- **Design — LOCKED: warm cream-paper editorial.** Cream `#f7f4ed` background (NO white cards), **Georgia serif** headlines + a centred quote block, **terracotta `#b85d3d`** accent, dark pill CTAs, hairline rules, circle "D" badge masthead. Deliberately distinct from The Open Source.
- Byline **Johana Buitrago** · From `dealmaker@send.usingaitoscale.com` · e.g. subject "The local deal is not the offer." Teach a preeminence principle → apply it to a real local situation → weave the offer in (never a hard pitch).

**2. The Open Source** — *editorial/informational via Donald-Miller storytelling; open-source AI vs big tech.*
- **Design: clean, PhantomBuster-style.** Light gray/white, **blue `#3b5bdb`** accent, gray feature cards, black pill CTA, generated open-padlock logo.
- Byline **Theo Marsh** · From `open-source@send.usingaitoscale.com` · e.g. subject "Open-source AI for the businesses big tech forgot." Reader = the small-business hero; builders = guides. **Credit the original authors:** the featured Hermes Agent is **Nous Research's** — link `github.com/nousresearch/hermes-agent`; keep `github.com/jbellsolutions` only as the footer "builders' work" line.

**3. The Referral Channel** — *independent-news; the referral economy, reported with a POV.*
- **Design: reuse its OWN Issue 1 design.** Dark `#0b0b0c` chyron masthead, blue `#2563a8`, white cards, dark footer. A strong Lead + Dispatches (NOT a grid of equal cards).
- Byline **Jay Bell** · From `referral@send.usingaitoscale.com` · e.g. subject "The affiliate link is becoming a newsroom beat."

**4. Local Affiliate Pro** — *story/StoryBrand; local "Main Street" businesses take back their power.*
- **Design — LOCKED: the "Angliss" magazine template.** Dark photo hero + orange `#ea6b23` logo box, condensed headlines, continuous story (lead + 3 illustrated beats, one CTA).
- Byline **Jordan Reyes** · From `local-affiliate-pro@send.usingaitoscale.com` · subject "Main Street's unfair advantage" · CTA `localaffiliatepro.com/agencies/`.

## General craft rules (all newsletters)
- **Apply a supplied design template FAITHFULLY.** Keep its style/layout/fonts/colors/formatting; strip 100% of the source brand; remove parts we can't fill; **invent NO new design elements** — no left-border quote bars, no colored callout boxes, no dark panels that aren't in the template. Invented decoration = AI slop.
- **Greeting = "Hi {first name}," + a fallback** (ListMonk: `{{ if .Subscriber.FirstName }}{{ .Subscriber.FirstName }}{{ else }}there{{ end }}`) — never "good morning," never a blank "Hi ,". Headline-led news titles with no greeting line may skip it.
- **Restrained emphasis:** bold the few key stats/thesis lines + the design's accent color on ~1 phrase per issue. Not a highlighter dump.
- **Images:** editorial craft (Monocle / Bloomberg register), never literal-metaphor AI slop; **never blank paper** — any label/doc gets realistic soft-focus print. Xander generates all images; you only write prompts (detailed, text-safe, with generation + display sizes).
- **No fabrication.** Every stat/quote traces to a real source (browser-verify, not curl). **Never** print "AI Integraterz" / "Published by AI Integraterz"; never "power partner" (→ "affiliate program"); footer = own name + physical address `37460 Beacon Brick Road, Zephyrhills, FL 33541` + unsubscribe, **no socials, no false "you subscribed" line.**
- **Link-reputation gate (before ANY send):** check every CTA/link domain on Google Safe Browsing + run mail-tester; no flagged links, no ephemeral `*.here.now`/free-subdomain CTAs. *(LAP's `localaffiliatepro.com` is currently flagged — do NOT send it until Justin clears it.)*
- **List hygiene:** verify lists before send (bounce <1%, complaints <0.1%), suppress bounces.

## Niche / industry titles (Front Desk, Protocol, Green Room, People Person, Daily Sun, Agency Insider)
**Pure education — NO native ad card, NO bottom CTA, NO affiliate mentions.** Build trust only; each gets its own distinct look.

## Do this now
1. **Update your per-newsletter skills + general newsletter skills** to match everything above.
2. **Then LIST every newsletter-related skill you currently have** — name + a one-line description each — so we can confirm you digested this. Flag anything that conflicts with the above.
