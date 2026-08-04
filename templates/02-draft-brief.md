# Stage 2 â€” Draft Brief (template)

## FILL THESE IN FIRST

*(Operator note, safe to leave in the pasted prompt.)*

| Placeholder | What to put in it | Where to get it |
|---|---|---|
| `{{NEWSLETTER_NAME}}` | e.g. `The Protocol` | `CLAUDE.md`, "The Five Newsletters" |
| `{{BRAND_EMOJI}}` | One emoji, the same one every issue. e.g. `ðŸ§¬` | Same table |
| `{{TAGLINE}}` | e.g. `The business of helping men live their 50s like their 20s.` | Same table |
| `{{AUDIENCE}}` | The greeting noun plus who they are. e.g. `operators â€” clinic owners, telehealth founders, coaches` | Same table |
| `{{RESEARCH_FILE}}` | Absolute path to the stage-1 output | `RESEARCH-<NICHE>-NEWSLETTER.md` |
| `{{STORY_LINEUP}}` | The five news stories by research-file number and title, in running order, with card 3 left for the house item. e.g. `Card 1: #1 FDA Panel Weighs Seven Peptides Thursday Â· Card 2: #3 Telehealth Rules Expire Â· Card 3: HOUSE Â· Card 4: #7 Hims Â· Card 5: #10 GLP-1 Persistence Â· Card 6: #9 Hone Health` | The "Recommended five" section of the research file |
| `{{HOUSE_ANNOUNCEMENT_CONTENT}}` | What the house announcement is announcing â€” the capability, offer, result, or asset, with its real mechanics. It does not have to be new. | The client, plus any published article being used as its "source" |
| `{{OFFER_URL}}` | The live destination card 3 and the house blurb link to | Client. **Blocking â€” never paste this unresolved** |
| `{{UTILITY_SEGMENT_TOPIC}}` | The free teaching piece. e.g. `The three channels that work when you can't run ads` | Pick something the reader can act on with no purchase |
| `{{COMPANY_NAME}}` | e.g. `AI Integraterz` | `CLAUDE.md`, "Key Facts and Links" |
| `{{PHYSICAL_ADDRESS}}` | e.g. `37460 Beacon Brick Road, Zephyrhills, Florida 33541` | Same |
| `{{ISSUE_DATE}}` | e.g. `Thursday, July 23, 2026` | The send date, not today |
| `{{OUTPUT_FILE}}` | e.g. `...\Newsletter\PROTOCOL-ISSUE-1.md` | Convention: `<NAME>-ISSUE-N.md` in the working directory |

---

## PASTE FROM HERE

You are writing one complete issue of **{{NEWSLETTER_NAME}}** {{BRAND_EMOJI}} â€” *{{TAGLINE}}* â€” for {{AUDIENCE}}.

This is an outbound newsletter: a cold email built as a genuine trade publication. The reader must experience a real publication, not a sales email. Write **{{OUTPUT_FILE}}**. Derive the issue number from that filename.

### The one rule everything else serves

**Card 3 is the house announcement, and it is formatted identically to the news cards around it. This is non-negotiable.**

Same category label, same emoji weight, same clickable headline, same image slot, same three-part body, same `Read more â†’`. No "sponsored" label. No tonal shift. No second person. No adjectives of excitement. A reader scanning the issue must process it as the third news item of the day.

It sits at **position 3 of 6** â€” never last. Last is the ad position; the middle is the editorial position. It does not have to be news: any real capability, offer, result, or asset can be written up as an announcement.

If your card 3 reads like a pitch, the issue has failed regardless of how good the rest is.

### Sourcing

**Every fact, number, date, quote, and name in this issue comes from {{RESEARCH_FILE}}.** No exceptions, no memory, no "commonly known" figures, no rounding a range into a single number. If a fact is not in that file, it does not appear in the issue.

Carry the research file's caveats forward. A source flagged **Secondary** there stays flagged in your Sources table here. A figure the file says is point-in-time gets dated in the copy rather than presented as current. A number the file says not to publish does not get published.

Card 3 is the only block not sourced from the research file. Its content is: {{HOUSE_ANNOUNCEMENT_CONTENT}}. It must contain **zero external factual claims** â€” describe mechanics you control, not market statistics.

### The story lineup

{{STORY_LINEUP}}

### Format spec â€” build exactly this

```
SUBJECT      {{BRAND_EMOJI}} + lead story headline, under 55 characters
PREHEADER    Plus: [story 2], [story 4]

MASTHEAD     {{BRAND_EMOJI}} {{NEWSLETTER_NAME}}
             {{TAGLINE}}
             Issue #N Â· lead headline
             By {{NEWSLETTER_NAME}} Â· {{ISSUE_DATE}}
             Read Online | Unsubscribe
BANNER       s0 â€” branded banner image, not a story image

GREETING     "Good morning, {{AUDIENCE}}."
THESIS       ONE sentence of point of view that frames the whole issue
TOC          "In today's {{NEWSLETTER_NAME}}:" + 5 bullets

DIVIDER      LATEST DEVELOPMENTS

CARD 1       news story
CARD 2       news story
CARD 3       â˜… THE HOUSE ANNOUNCEMENT â€” identical formatting, links to {{OFFER_URL}}
CARD 4       news story
CARD 5       news story
CARD 6       news story

DIVIDER      THE PLAYBOOK
UTILITY      {{UTILITY_SEGMENT_TOPIC}} â€” free teaching, image s7, closing link to {{OFFER_URL}}
HOUSE BLURB  2-3 italic lines on what {{COMPANY_NAME}} does + one link  â† second and final mention

DIVIDER      KEEP READING
KEEP READING 3 teasers, each a bold link + an italic "Plus: ..." subline

SIGN-OFF     A named human + their title
FOOTER       {{COMPANY_NAME}} Â· {{PHYSICAL_ADDRESS}} Â· disclaimer Â· honest cold-receipt line +
             unsubscribe Â· preference option Â· Primary-tab ask
```

### The story formula â€” every card, including card 3

```
CATEGORY LABEL                       small all-caps, e.g. FDA Â· MARKET Â· RETENTION
[emoji] **[Headline](source URL)**   the headline itself is the link, not just "Read more"
[IMAGE â€” sN: one-line art direction]

**The Short Version:** One paragraph, 55-85 words, subject-first and factual. What happened, plainly.

**The Details:**
- 4 bullets of specifics: numbers, dates, exact quoted language where it matters.
- Include the correction a reader is most likely to have wrong.

**Why It Matters:** One paragraph of analysis. What this changes for the reader's business.
This is where the publication earns authority. It is also the only legitimate place for a house point of view.

Read more â†’ https://...
```

The headline link and the `Read more â†’` link point at the same URL. Both are clickable â€” half the click surface is lost otherwise.

**Do not upgrade a card's format beyond what its source supports.** If the research only carries a summary, write a summary; inventing "The details" bullets or a "Why it matters" the source does not support is a fabrication, not a format fix. A format upgrade never justifies unsourced copy.

### Copy rules

- **Numbers carry the weight.** Specificity is the credibility. `$113.53 million ARR`, `33,607 patients`, `60.9%` â€” not "significant growth."
- **Zero hype vocabulary.** No "game-changing," "revolutionary," "imagine if," "supercharge," "unlock," "transform." The news is the news.
- **Banned words, verify absent before you finish:** game-changing Â· unlock Â· revolutionize Â· imagine if Â· supercharge.
- **One idea per paragraph, 1-3 sentences.** Mobile-first throughout.
- **The reader is an operator**, never a "subscriber" or "friend."
- **The house item uses the same register as the hardest news item in the issue.** Flat, factual, unexcited.
- **No reply-based calls to action.** Every CTA routes through a link.

### Mention budget: exactly 2

Card 3 and the bottom house blurb. That is the entire budget. One is a wasted send; three is an ad. The footer legal line and the utility segment's closing link are boilerplate and navigation, not mentions â€” but do not use them to smuggle in a third pitch.

### Spam-word discipline

Scan the finished draft against: buy Â· cash Â· money Â· sale Â· promotion Â· free Â· discount Â· cheap Â· earn Â· income Â· profit Â· guarantee Â· act now Â· limited time Â· urgent Â· click here Â· order now Â· special offer Â· risk-free Â· no obligation Â· winner Â· congratulations Â· miracle Â· amazing Â· 100% Â· credit card

**The rule is minimise, not ban.** These newsletters report on business, so some hits are legitimate financial reporting. What reads as spam is density and register â€” sales language in a sales context. News language in a news context is fine. Fix on sight:

- Category labels: never `MONEY`. Use `MONETIZATION`, `REVENUE`, or `ECONOMICS`.
- Two trigger words adjacent (e.g. "free cash flow") â€” rewrite or cut. That pairing is the strongest signal.
- The same trigger word twice within a few lines â€” vary one.
- **Your own copy â€” the thesis, the utility segment, card 3, the house blurb â€” must be clean.** You control it entirely. Sourced story copy gets more latitude, because rewriting a quote risks accuracy.

### Also required in {{OUTPUT_FILE}}

After the issue itself, add these sections. They are what the image and HTML stages read.

1. **Subject line options** â€” 5 candidates, all carrying {{BRAND_EMOJI}}, all under 55 characters, character counts shown, one recommended with a reason.
2. **Preview text** â€” one line, `Plus: ...`, naming two stories that are not the lead.
3. **Staging notes â†’ Placeholders** â€” a table of every double-brace token left in the file, where it appears, and what resolves it. `{{UNSUBSCRIBE_LINK}}` and `{{VIEW_ONLINE_LINK}}` stay as tokens â€” the ESP maps them to its own merge tags. Anything else left as a token is a blocking item and must be labelled as one.
4. **Staging notes â†’ Image slots** â€” a table of all 8 slots (s0 banner, s1-s6 cards, s7 utility) with a one-line art direction each. Read the eight together before finalising: **never brief two slots with the same subject.** Add the note that s3 is the house image and must sit inside the same visual set as s1-s6.
5. **Staging notes â†’ Links** â€” every outbound URL, and which of them have been fetch-verified.
6. **Items needing human verification before send** â€” dates, figures from blocked primary sources, anything the research file flagged as unresolved. Say what breaks if it is wrong.
7. **Other pre-send checks** â€” named sign-off confirmation, cold-send posture, compliance read for the niche, banned-vocabulary confirmation, and a format-parity note on card 3.
8. **Sources used** â€” a table: card number, story, source link, and the caveat carried forward from the research file. Then a short paragraph on which research items you deliberately did **not** use and why.

### Done means

Six cards with card 3 indistinguishable from the rest, every number traceable to {{RESEARCH_FILE}}, exactly two house mentions, banned words verified absent, the spam-word scan run, and eight image directions that do not repeat a subject.
