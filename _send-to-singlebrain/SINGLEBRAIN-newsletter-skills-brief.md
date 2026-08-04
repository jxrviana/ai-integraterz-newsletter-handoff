# → SingleBrain: teaching you the newsletter pipeline end-to-end

*(Xander: paste the message below to SingleBrain in Slack, and attach the files listed in "FILES TO ATTACH." The message is written to SingleBrain.)*

---

## FILES TO ATTACH (drop these with the message)

**For the skills (the system):**
1. `NEWSLETTER-PLAYBOOK.md` — the format + build spec (backbone of the process skill)
2. `newsletters/00-SOURCE-OF-TRUTH.md` — strategy, structure, KPIs, footer rule, SMTP stack
3. `offers/OFFER-affiliate-program.md` — the offer every newsletter pitches
4. `newsletters/the-referral-channel.md` — identity of newsletter #1
5. `newsletters/the-dealmaker.md` — identity of newsletter #2

**Gold-standard worked example (a finished issue, start to finish):**
6. `ready-to-send/the-referral-channel/THE-REFERRAL-CHANNEL-ISSUE-1.md` — the source copy
7. `ready-to-send/the-referral-channel/index.html` — the finished email HTML
8. `ready-to-send/the-referral-channel/medium-article.html` — the finished Medium article

*(Hold `newsletters/main-street-affiliate.md` until we build that one — it's a future Beehiiv build.)*

---

## THE MESSAGE (paste this to SingleBrain)

Hey SingleBrain — I'm setting you up to run our newsletters **end-to-end**, from research all the way to the send. Right now Claude hand-builds each issue; we're packaging that process as skills so you can run it at scale. Claude stays as architect + final QA; you execute the pipeline.

**1) Build these skills from the attached files — do NOT dump everything into one skill.** One giant skill makes you blend newsletters and hallucinate. Split it like this:

- **`newsletter-pipeline`** (the master process skill — the HOW). Build from `NEWSLETTER-PLAYBOOK.md` + `00-SOURCE-OF-TRUTH.md` + `OFFER-affiliate-program.md`. This holds the end-to-end process, the universal email format, every hard rule, the QA checklist, and the send steps. This is the skill that does the work.
- **`the-referral-channel`** (a newsletter's identity — thin). Build from `the-referral-channel.md`. Just: name, angle, audience, CTA, format register. It calls `newsletter-pipeline` for the process.
- **`the-rainmaker`** (a newsletter's identity — thin). Build from `the-dealmaker.md`. Same thin structure.

Rule of thumb: **the process lives in ONE skill; each newsletter's identity is its OWN thin skill.** That keeps the process consistent and stops the newsletters from bleeding into each other. When we add more newsletters (Main Street Affiliate, and the niche ones), each gets its own thin identity skill — don't create those yet.

**2) The pipeline `newsletter-pipeline` runs (this is the whole job):**
1. **Research** — find real, current stories/stats for the issue. **EVERY stat must trace to a real fetched source (a URL). No fabrication, ever — this is rule #1.**
2. **Copy** — write to the playbook format (editorial = six news cards with the native house card at position 3; direct-response = a persuasive letter). No emoji, no hype/spam-word density, HTML entities for punctuation, exactly one hidden preheader div.
3. **Images** — photorealistic editorial photos, one per slot, a different look per image, text-safe surfaces. ⚠️ **If you can't generate images, STOP and tell us** — Claude will make them in Higgsfield and hand them back. Don't ship without real images.
4. **HTML** — email-safe build (600px tables, inline styles, ASCII-only).
5. **Medium article** — the paste-ready HTML article that the house card links to, **plus 5 Medium tags handed over every time**.
6. **QA** — trace every number to its source; check the house card is byte-identical to the news cards; check links + placeholders; run the spam-word scan; render-check.
7. **Test send** — to `xander@usingaitoscale.com` + `justin@usingaitoscale.com` ONLY.
8. **STOP — approval gate.** Do **NOT** send to the list until Xander (and Justin) approve. This gate is mandatory on every issue.
9. **Send** — on approval, send to the list via ListMonk (Bird/Resend), seeded with the two internal addresses.

**3) Hard rules — bake these into the skills:**
- No fabricated facts. Every stat cites a fetched source, or it doesn't ship.
- No AI slop — specific, real, high-quality content only.
- **Nothing goes to the list without explicit approval** (test send + approval gate first), every time.
- **Footer: NO social links.** Brand the footer to the newsletter's own name (e.g. "The Dealmaker"), and keep "Published by AI Integraterz" + the physical address + the unsubscribe link.
- The offer is an **"affiliate program"** — **never** call it "power partner."
- No emoji anywhere. From display-name = the newsletter's name. Reply-To = `xander@usingaitoscale.com`. Seed every send with the two internal addresses.

**4) Start with ONE newsletter as a pilot — don't run all of them at once.** Do **The Referral Channel** end-to-end first. It's fully built and its Medium article is already published, so you have a complete gold-standard example (attached: its source copy, its finished `index.html`, and its Medium article). Study those, produce the next issue to that same quality, we validate it — THEN we scale to The Dealmaker and the niche newsletters.

**5) Key facts you'll need:**
- Sending engine: **ListMonk**, SMTPs = **Bird #1 + Resend #2**. Sending domain `send.usingaitoscale.com`. From display-name = the newsletter's name. Reply-To = `xander@usingaitoscale.com`.
- Seed every send with `xander@usingaitoscale.com` + `justin@usingaitoscale.com`.
- CTA / offer link: `cal.com/usingaitoscale/aiintegraterz` (fallback) → `mainstreetaffiliate.com` when it's live.
- Medium accounts: `@ai_integraterz` (affiliate + men's health) and `@hiring_65676` (recruiting) — Xander publishes.
- Legal footer line: AI Integraterz · 37460 Beacon Brick Road, Zephyrhills, Florida 33541.
- Send lists: Xander provides the verified list per issue (from `leads/final-list/`).

**6) Report back:** tell us which skills you created and how you structured them, and flag anything you can't do yourself — **especially image generation** — so we keep that step with Claude.

Thanks — excited to get you running these.
