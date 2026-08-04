# Newsletter Production Templates

Five reusable agent briefs. Together they take one newsletter issue from "we need an issue" to "a rendered HTML file with images, ready for the ESP" — without anyone re-authoring the instructions.

Each brief was extracted from the prompts that actually produced the five newsletters on disk. Every rule in them traces to `NEWSLETTER-PLAYBOOK.md` or to `CLAUDE.md`. Those two files remain the source of truth; these templates are the delivery mechanism.

---

## The order

| # | File | Who runs it | Produces |
|---|---|---|---|
| 1 | `01-research-brief.md` | Research agent (Opus) | `RESEARCH-<NICHE>-NEWSLETTER.md` — 10-12 verified story candidates + a recommended five |
| 2 | `02-draft-brief.md` | Writing agent (Opus) | `<NAME>-ISSUE-N.md` — the full issue in markdown, every fact sourced |
| 3 | `03-image-brief.md` | Image agent (Opus, Higgsfield) | `<name>-issue-N/images/` — 8 photorealistic images, s0-s7 |
| 4 | `04-html-build-brief.md` | HTML agent (Opus) | `<name>-issue-N/index.html` — email-safe, images wired in |
| 5 | `05-qa-checklist.md` | You, or a QA agent | A pass/fail report before anything is handed to the ESP |

Stages 3 and 4 both depend on stage 2, but not on each other. Run them in parallel if you want — the HTML agent writes `images/sN.jpg` paths whether the files exist yet or not.

**Verify every stage's output before starting the next one.** A bad statistic in stage 1 becomes a bad statistic in the sent email; nothing downstream catches it for you.

---

## How to fill a template

1. Open the brief. The **FILL THESE IN FIRST** table at the top lists every placeholder in that file and where to get its value.
2. Find-and-replace each `{{PLACEHOLDER}}` — braces included — with the real value.
3. Search the file for `{{` one last time. Anything left over — other than the two output tokens below — is one you missed.
4. Paste the whole file as the agent's prompt. No other editing needed. The operator table at the top is harmless to leave in.

### Two tokens you do NOT replace

`{{UNSUBSCRIBE_LINK}}` and `{{VIEW_ONLINE_LINK}}` are **output** tokens. They are supposed to survive into the finished markdown and HTML, where the ESP swaps in its own per-recipient merge tags at build time. Leave them alone everywhere they appear.

`{{OFFER_URL}}` is different — it is an input. If you paste it unresolved, the issue cannot send, because driving clicks to that URL is the entire point of the card-3 mechanic.

---

## Standing rules that apply to every stage

Carried from `CLAUDE.md`. Each brief repeats the ones it needs, but they hold whether or not a brief restates them.

- **No fabricated facts, ever.** Every statistic traces to a real fetched source. If it cannot be verified, it does not ship.
- **Work only inside the newsletter working directory.** Never read or search `Downloads`, `Desktop`, `Documents`, or anywhere else on the machine — not even to find a file someone mentioned. Ask for it to be placed in the working folder instead.
- **Nothing sends without explicit approval.** These templates produce drafts and test files. Sending, publishing, and deploying are separate decisions made by a human in the moment.
- **Every issue ships as a rendered HTML file with images.** Markdown alone is a half-finished issue.
