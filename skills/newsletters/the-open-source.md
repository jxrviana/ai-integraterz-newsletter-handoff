# Newsletter Skill — The Open Source

*Per-newsletter identity skill. Use with the general skills (`00-pipeline`, `01-creation-and-QA`, `05-images`). NEW build. Editorial / informational, delivered through **Donald Miller StoryBrand** storytelling — NOT the 6-card news roundup and NOT a direct-response letter. It's a story-led feature built around ONE real open-source tool per edition.*

## Identity
- **Brand:** The Open Source
- **Tagline:** "Open-source AI for the businesses big tech forgot." *(alt: "We build the AI, give it away free, and teach you to run it.")* — lock one at design.
- **Type:** Editorial / informational (Justin's taxonomy), told as StoryBrand storytelling.
- **Mission (the movement people join):** level the playing field — push back against big AI + big tech trying to own the future. A small crew of builders makes real AI systems, gives them away **FREE**, and teaches people to run them, so small + local businesses can **fight back** and automate cost-effectively.
- **Byline:** Theo Marsh *(PLACEHOLDER — confirm/swap. Keep a builder-editor persona, distinct from every other newsletter's byline.)*
- **From:** `The Open Source <open-source@send.usingaitoscale.com>` *(⚠️ confirm the local-part — `open-source@` works; `builders@` / `hq@` are also on theme.)*
- **Reply-To:** `xander@usingaitoscale.com`
- **CTA:** `https://whimsy-nebula-47ch.here.now/` (current standard) — **soft only.** This is education-first; the real "yes" is engaging with the mission / grabbing the free tool. See Open decisions on whether to run the standard CTA at all or point to the tool instead.
- **SMTP:** TBD — Justin assigns. SendFox is the new active channel for adding volume; Bird / Resend also available. Xander doesn't own the infra — tell Justin what's needed.
- **Masthead:** its own distinct superhero / open-source identity (own logo, own emoji, own colors) — see Design & branding. Shares NOTHING visual with the other newsletters.

## The hook / angle
The founder's true story, and the reason this exists: **"199 projects later, you realize AI is only being sold to enterprise"** — while every normal business is scrambling to actually *use* AI to run the day-to-day. There are a bajillion AI agencies and self-proclaimed experts selling slide decks; we actually **built real software** — for ourselves and for clients — and we're handing it over. That contrast (**sold-to-enterprise** vs. **built-and-given-away**) is the recurring spine of the whole publication.

## StoryBrand framing (get this right)
The **reader is the HERO; we are the GUIDE.** (Most common failure: making *us* the hero — don't.) The "superhero" theme lives in the **branding and visuals** — the small crew of builders as the team that *arms* the underdog — but in the **copy** the small/local business is always the one who wins. Map every edition to the StoryBrand arc:
1. **Character (hero):** a small/local business owner who wants to compete but is priced out of "enterprise AI."
2. **Problem:** external = can't access/afford the tools; internal = "AI isn't built for people like me / I'm falling behind"; villain = big AI + big tech hoarding the advantage.
3. **Guide (us):** empathy ("we ran 199 projects and hit the same wall") + authority ("so we built the software ourselves").
4. **Plan:** here's a real tool, here's exactly how it works, here's how you run it.
5. **Call to action:** grab it / use it — soft, because it's free and open.
6. **Avoids failure:** staying stuck, priced out, dependent on the giants.
7. **Ends in success:** a small business running enterprise-grade automation for free.

## Source material — Justin's GitHub
- **`github.com/jbellsolutions` (109 repositories).** Each edition picks ONE real repo/tool and molds it into a story: the problem it solves, why it was built, how a small business puts it to work.
- **BLOCKER — no fabrication:** actually inspect the repo (README / code) before writing. Describe only what it really does; never invent features, metrics, or a backstory. (Core project rule: every fact traces to a real source.) If a repo can't be verified or understood, pick another.
- Keep a running log of which repos have been featured so editions never repeat.

## Per-edition structure (keep the formatting craft Justin loves)
Keep the craft Justin praised — good-morning intro, bolds/italics, "The Short Version / The Details / Why It Matters," quote blocks, image-as-format — but tell it as ONE story, not six cards.
1. **Masthead** — brand + emoji + tagline + `Issue 00X · Month Year` + `Read online | Unsubscribe`.
2. **Hero banner image** — superhero / underdog theme (see Design).
3. **Good-morning intro** (2–3 lines) — name the hero (the reader) and the villain (big AI / big tech).
4. **One POV thesis line** — the mission in a single sentence.
5. **The Problem** — the reader's world and why the giants hold the edge. Open on the pain.
6. **What we built** — the origin story of this edition's repo/tool (the 199-projects journey; why THIS, not vaporware). Use "The Short Version / The Details / Why It Matters" to describe the tool.
7. **How it works** — plain-English walkthrough (the Plan). A diagram or clean screenshot image.
8. **Put it to work** — the concrete step a small/local business takes this week (the transformation).
9. **Build-along / free tip** — a utility segment that teaches something usable for free (mirrors the general playbook's utility block).
10. **Soft close** — it's free and open; a light nudge (grab the tool / reply). No hard sell.
11. **Named sign-off** (byline) → **compliant footer**.

## Design & branding (NEW — to lock; nothing is locked yet)
Universal direction (Aug 4 huddle — applies to ALL newsletters):
- **White background** (drop all brown / black-brown — white reads more professional).
- **Wider layout** (less of the narrow centered 600px column).
- **Its own look** — must NOT share fonts, colors, logo, or image style with any other newsletter. A reader who gets two of ours the same day should never guess they came from one sender.

Distinct to The Open Source:
- **Superhero / comic direction on a clean white page** — bold, high-contrast, heroic. To explore at design: an ink-black display headline face + one bold "heroic" accent (electric blue or a comic red) + a bright secondary; tasteful comic/print touches (halftone, panel borders, a hint of action) — energetic, not cartoonish. Lock palette + type at the design pass.
- **Logo:** its own emblem on the open-source / hero idea — e.g., a shield or crest built from `</>`, a fork symbol, or a terminal cursor: a "builders arming the underdog" mark. Claude briefs; Xander generates.
- **Emoji:** one on-theme masthead emoji (shield / mechanical-arm / rocket family) — lock at design.

## Images (Xander generates — see `05-images`)
- **Theme:** a small crew of builders arming the underdog; the small/local business as the hero stepping up. A distinct style from every other newsletter — explicitly NOT the "canned / vintage / same-source" look Justin flagged. Consider a consistent comic/heroic treatment as this title's signature.
- Claude writes text-safe prompts; **Xander generates every image** (Claude / SingleBrain never generate images). Typically a banner + 1–2 in-story visuals (the how-it-works diagram or screenshot can be a clean graphic).

## Cadence
Aspirational (Justin): up to **~3 companion articles + ~2 editions per week.** Start at **1 edition/week** until the format and design are proven, then scale. Companion articles can seed editions, or vice-versa.

## Compliance & build
- No "AI Integraterz" / "Published by AI Integraterz" anywhere. Footer = **The Open Source** + physical address `37460 Beacon Brick Road, Zephyrhills, Florida 33541` + Unsubscribe. **No social links.**
- Never "power partner" (→ "the affiliate program," and even that stays soft here). No banned words: game-changing, unlock, revolutionize, imagine if, supercharge. No false relationship claims — this is cold outbound (never say "you signed up").
- Email-safe HTML: **inline all CSS** (no `<head><style>` block — clients strip it), ASCII / HTML entities only, merge tags `{{ MessageURL }}` / `{{ UnsubscribeURL }}`.
- Every fact/feature traces to the real repo. Run `01-creation-and-QA` before any delivery.
- Draft + test send only; **Xander approves before any real send.**

## Open decisions (resolve before Issue 1)
1. **Byline** — confirm or replace `Theo Marsh` (placeholder).
2. **From local-part** — confirm `open-source@` vs `builders@` / `hq@`.
3. **The "free tool" destination** — pointing readers straight to `github.com/jbellsolutions` exposes the shared operator handle and dents the separate-publication wall. Options: mirror featured repos under an Open-Source-branded org, gate behind a soft reply, or describe + offer on request. Decide before we promise "free" with a live link.
4. **CTA** — keep the standard `whimsy-nebula` CTA (soft) or replace it with the free-tool destination? Education-first logic says: lead with the tool, keep any affiliate CTA minimal.
5. **Design lock** — palette, type, logo, and emoji all pending a design pass.

## Status (2026-08-05)
**NEW — to build.** Concept locked from the Aug 4 huddle; design + first issue pending. No issue drafted yet. Next steps: lock the design direction (white bg, wider layout, superhero look), pick the first `jbellsolutions` repo, and draft Issue 1 against this skill + the general library.
