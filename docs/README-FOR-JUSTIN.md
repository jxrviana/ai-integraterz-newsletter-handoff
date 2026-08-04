# Newsletter System — documentation package

Everything needed to produce an outbound newsletter and get it delivered, written so it can be handed to any agent or person and executed without the original context.

---

## Read in this order

**1. `SKILL-newsletter-production.md`** — start here.
The complete build procedure. What the product is, the inputs required before starting, the five stages (research → draft → images → HTML → QA), the quality rules, and a table of every mistake made building the first five issues with the rule each one produced. Give this to an agent along with a niche and an offer and it can produce an issue to standard.

**2. `templates/`** — the reusable prompts.
Six files. One agent brief per stage with fill-in-the-blank placeholders, plus a QA checklist. Producing the next newsletter is filling in blanks, not writing instructions from scratch.
`00-README.md` · `01-research-brief.md` · `02-draft-brief.md` · `03-image-brief.md` · `04-html-build-brief.md` · `05-qa-checklist.md`

**3. `DELIVERABILITY-RUNBOOK.md`** — the platform-agnostic sending process.
How SPF, DKIM, DMARC and reverse DNS actually work and what each proves. A universal setup checklist for standing up any new sending platform. The 10-lookup limit and why it constrains switching. Three levels of testing. Cold-domain warming. Gmail and Yahoo bulk-sender requirements. A platform-switch runbook. A troubleshooting table. Our JangoMail setup is the worked example, including what went wrong.

**4. `NEWSLETTER-PLAYBOOK.md`** — the format spec.
Where the format came from: four reference newsletters (MyClaw, The Rundown AI, The Future Today, There's An AI For That) pulled apart and rebuilt into a house standard. Includes the native-announcement rule, copy rules, spam-word discipline, and the image production rules.

---

## The two rules everything else serves

**The house announcement is a story, not an ad.** It sits at position 3, formatted byte-identically to the news around it — same category label, same headline weight, same image, same structure, no sponsored tag. Parity is verified programmatically by diffing style attributes, never by eye. Exactly two mentions per issue: that card and one short blurb near the bottom.

**Nothing unverified ships.** Every statistic traces to a page that was actually fetched. Vendor research is labelled as vendor research. Where a primary source was blocked, the secondary is flagged as secondary. A format upgrade never justifies unsourced copy — one issue deliberately uses a simpler story format because its sources could not support the richer one.

---

## Current state

Five newsletters built: The Protocol (men's health), The People Person (recruiting/staffing), The Daily Sun (solar), The Bow-legged Mechanic (HVAC), The Green Room (PR agencies).

Deliverability: 10/10 on mail-tester across all three sending issues, up from 3.6. SPF, DKIM and DMARC all passing. One-click unsubscribe confirmed present.

---

## Not included

`CLAUDE.md` and `HANDOFF.md` are internal operating context for the AI session — standing rules and current-state tracking. They are working files, not deliverables.

`DELIVERABILITY-FIX-PLAN.md` is the underlying sourced research behind the runbook. Available if you want the citations, but the runbook is the usable version.

---

## Known gaps, stated plainly

**The quality bar is not locked.** These are living documents. The newsletters will keep improving and these files get updated as they do — nothing here should be treated as final.

**The warm-up ramp schedule is professional practice, not a documented rule.** No mailbox provider publishes one. It is labelled as such wherever it appears. The complaint-rate threshold (0.3%) *is* documented by Google and Yahoo; the bounce threshold (2%) is our own.

**Two newsletters are built but unscheduled** — The Daily Sun and The Bow-legged Mechanic. **Two niches are not started** — The Power of Partners and Skool groups. **One draft predates the playbook** — the Agency Insider, which needs a rebuild before it could ship.
