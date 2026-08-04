# Newsletter Task — Plain-English Breakdown
*For Xander · built from Justin's brief + both zip folders · July 17, 2026*

---

## 1. The TLDR (one paragraph)

Justin is launching an **in-house newsletter publishing company that is run by AI agents** — and you are the human operator. The AI agent team already exists (the Overdeliver folder). The business plan already exists (the Open Source folder). The email-sending tools are already connected. Your job is to **assemble the pieces, feed them content, and launch test newsletters on Monday** so the team can measure which email platform actually lands in inboxes. You don't need to invent anything — you need to connect, upload, instruct, and oversee.

**Deadline: "Friday Ready, Monday Launch"** — set up ready by end of Friday, first real sends Monday (July 20).

---

## 2. Who's who (the glossary — learn these 8 names)

| Name | What it actually is | Your relationship to it |
|---|---|---|
| **governance** | Justin's custom agent-management platform (his modified version of "Paperclip"). It hosts and runs a whole team of AI agents. | You create your access via his invite link, create projects, and upload the agent files into it. |
| **SingleBrain** | The AI agent living in your Slack, assigned to you. Already connected to the 3 email platforms. | You give it instructions in the SingleBrain Slack channel. Justin watches that channel so he can help. |
| **Bird** | Email platform #1 — the **burner**. Cheap blast tool. Justin doesn't care if it gets flagged. | Use it for the first big test: upload leads, blast a newsletter, see what happens. |
| **Jango** | Email platform #2 — the **middle ground**. Expensive, so it must produce leads to justify its cost. (The planning docs spell it "Django.") | Send a fairly high-quality newsletter through it. Don't trash it, don't baby it. |
| **Autosend** | Email platform #3 — the **keeper**. Long-term platform. Needs a domain connected, then slow careful warm-up. Also used for transactional email + SMTP. | Treat with maximum care. Slow warm-up, highest quality newsletter, never burn it. |
| **Custom server** | Justin's own email server (almost finished). Cheapest, fully controlled. | Nothing yet — it's the future main platform. The current test decides what happens until then. |
| **Super Browser** | The team's browsing/scraping tool (Justin's "super-saiyan-browser" project). | Ask SingleBrain to use it to pull articles/links/content for newsletter issues. |
| **Hermes Mac1** | Another AI app inside Slack, good at making newsletters look good. | Optional — use it (or SingleBrain) for formatting/polish. |

**Why 3 email platforms at once?** It's a deliverability bake-off. An email that doesn't reach the inbox doesn't exist. Whichever platform delivers best wins the volume (and if the expensive one delivers best, it's worth the money).

---

## 3. What's actually in the two folders your boss sent

### 📁 "The Open Source" (the business plan — 12 documents)
The strategy for **three flagship newsletters** under one publishing house (publisher persona: **"AI Guy"**):

1. **The Open Source** — daily (M–F). Features one of Justin's open-source projects per issue, story-led, plus trending projects from elsewhere. Purpose: give real working systems away free → drive traffic and consulting leads.
2. **The Equalizer** — 2–3×/week. For small-business owners: how to adopt AI safely and cheaply without getting locked in by big providers. Mission-driven: "level the playing field."
3. **The Alpha** — weekly. Early releases and alpha-stage projects (some are Justin's, unbranded). Readers reply "IN" to become testers → that's the lead-generation engine.

Also in there: the governance philosophy (based on the book *Overdeliver* by direct-mail legend **Brian Kurtz** — that's who Justin meant by "Brian Hurts"), plus build specs for a content scraper, email infrastructure, website, angles system, and brand-voice library. **Most spec builds are Justin's job, not yours** — they're background context for you.

Rules that matter day-to-day (from the governance doc):
- **The list is sacred** — permission matters, suppression list shared everywhere, complaints get removed instantly.
- **Nothing ships without editorial sign-off** — every issue passes the "Three-Test" (is the story true? is it useful? is it differentiated?).
- **No fake urgency, no hype, no tricks.** Long game.
- (Bird's cold blast is Justin's deliberate exception to all this — that's why Bird is the burner.)

### 📁 "Overdeliver Mail Agency" (the AI employee roster — ~70 agents)
A complete AI "company" ready to upload into governance:
- **Operational agents**: editor-in-chief, lead copywriter, deliverability engineer, domain-warmup engineer, list-hygiene, fact-checker, researcher, analytics, etc.
- **A "board of directors"** of legendary marketers (Dan Kennedy, David Ogilvy, Eugene Schwartz, Gary Bencivenga…) + a Brian Kurtz "CEO" agent — advisory personas.
- **Teams, projects, recurring tasks** (daily send, daily deliverability check, weekly promotion planning…), **doctrine** (41 rules), and **skills**.
- An example client package (Tony Gameday) showing what finished output looks like.

Justin's words: *"You really just upload it to governance, and it will run for you."* The folder's own deployment doc says it's upload **plus a short setup ritual** — all clickable, none of it is building agents:

1. Get the folder into governance (Justin's instance is live at the invite link — it may already be loaded; check what's there first).
2. If it's not built yet: paste the ready-made "provisioning message" (sitting in `ARCHITECT_MESSAGE.md`) into the platform's **Architecture Board** — that's what makes it construct the company.
3. Add API keys under **Settings → Secrets** (~10 keys — they come from Justin; several may already be set since he connected the email platforms).
4. Answer a built-in **8-question setup interview** (who the readers are, the offer, cadence…).
5. Manually **greenlight the `daily-send` routine** — nothing sends until a human says go.

Three more things worth knowing:
- **The package never mentions Bird, Jango, Autosend, or SingleBrain.** It was written for the governance platform itself (Paperclip/"GOVAAA" + Composio + OpenRouter). Justin's voice note is the newer layer on top — where they disagree, his voice note wins.
- **You are the approval gate by design.** The docs require the human owner's OK for: any campaign launch, any new spend, and any deliverability emergency. "Oversight" isn't a nice-to-have — it's your defined role.
- Fun connection: the example client inside (Tony Gameday) is a **Gameday Men's Health** clinic — the same men's-health world as the case-study PDFs in Justin's screenshot. Those case studies are the raw material for your industry newsletters.

---

## 4. Your boss's 5 KPIs (his actual checklist for you)

1. ☐ **Connect SingleBrain to governance** — and run things from the Slack channel.
2. ☐ **Industry newsletters** — one per target niche (from his screenshot): **recruiting/staffing, men's health, men's coaching, MCA, marketing agencies, AI agencies, HVAC, solar**. Each needs a fun brandable name — his examples: men's health → "The Alpha Mail," recruiting → "The People Person."
3. ☐ **Build the 3 flagship concepts** — The Open Source, The Equalizer, The Alpha.
4. ☐ **Create governance projects + upload the agents** (the Overdeliver folder). His note: "Everything has been created for the team — just need the content and oversight."
5. ☐ **Connect Notion + project management** — everything tracked and saved.

Plus the immediate test he described first: **a Bird campaign** — upload a list of leads, send a newsletter, measure deliverability.

---

## 5. Division of labor

### ✅ Things only YOU can do (I'll walk you through each)
- **Open the governance invite link** and set up your access: `137-184-151-136.sslip.io/invite/pcp_invite_kzwvucue` (account creation is yours to do, not mine).
- **Paste messages to SingleBrain in Slack** — I draft every message, you send and report back what it says.
- **Upload the Overdeliver agent files into governance** (clicking through their UI on your account — I'll prep the files and the steps).
- **Get missing pieces from Justin**: the lead list for the Bird blast, which domain to connect to Autosend, the Notion workspace, and what the `soulful-quill-nnww.here.now` "skill" link is for.
- **Give final approval on anything that actually sends** — no email goes out without your (and Justin's) explicit go.

### 🤖 Things I can do for you
- **Explain anything** in this stack at any depth, any time — no question is too basic.
- **Draft every SingleBrain instruction** — you copy-paste.
- **Name + design the industry newsletters** — fun names, positioning, issue structure for all 8 niches, following the boss's formula.
- **Write the actual newsletter issues** — drafts for the 3 flagships and the industry ones (I have specialist copywriting/email skills, and I'll spin up Opus 4.8 agents for bulk work to save your tokens).
- **Research content** for any niche issue (Opus 4.8 research agents on my side; SingleBrain uses Super Browser on the company side).
- **Build the Notion tracker** — I have direct Notion access from this workspace (KPI #5), with your go-ahead.
- **Read Slack** — I have a Slack connector here, so I can read the SingleBrain channel to see its replies and draft your next move.
- **Deliverability guardrails** — Autosend warm-up schedule, Bird blast sanity checks (unsubscribe link + sender address so it's legal), and the scorecard for comparing the 3 platforms.
- **Track everything** — this folder + my memory keeps the project state across sessions.

---

## 6. The plan (how we'll actually do this)

**Step 1 — Today (get "Friday Ready"):**
1. You open the governance invite link → create access → tell me what you see.
2. You send SingleBrain the kickoff message (§7 below) → paste me its reply.
3. Based on its answers we upload the Overdeliver agents / create governance projects (or run the 5-step setup from §3 if the company isn't built yet).
4. You ask Justin the open questions (§8).

**Step 2 — Weekend (content ready):**
5. I draft: Bird test newsletter + the first flagship issue(s) + industry newsletter names/concepts for approval.
6. We stage the Bird campaign with SingleBrain (list uploaded, content loaded — NOT sent).
7. I build the Notion tracker; we log everything so far.

**Step 3 — Monday (launch + measure):**
8. Bird blast goes out (with Justin's go) → watch opens/bounces/spam placement.
9. Autosend domain connection + warm-up begins (small, careful volumes).
10. Jango campaign staged/sent as the quality middle ground.
11. We record results → the deliverability scorecard tells Justin which platform earns the volume.

**Then repeat:** content in → issues out → data reviewed → newsletters added niche by niche.

---

## 7. Your first Slack message to SingleBrain (copy-paste)

> Hey SingleBrain — Xander here. I'm running the newsletter launch (Friday-ready, Monday-launch). Before I start assigning work, catch me up on three things:
>
> 1. **Platforms** — confirm you're connected to Bird, Jango, and Autosend. For each one, what can you do right now: create campaigns, upload lead lists, send, pull stats?
> 2. **Governance** — are you connected to the governance platform yet? If yes, list the projects you can see. If no, tell me exactly what you need from me to connect.
> 3. **Bird test** — first job will be a Bird campaign: upload a lead list and send a test newsletter to measure deliverability. List everything you need from me for that (lead list file + format, sender name/domain, subject line, content, anything else).
>
> Answer those three and we'll get moving.

Paste its reply back to me and I'll tell you the next message.

---

## 8. Questions to ask Justin (6, short)

1. **Bird lead list** — where is it (file/CSV?), and roughly what is it (cold scraped list? old leads?) so we stay on the right side of spam law (unsubscribe + address included)?
2. **Autosend domain** — which domain do we connect, and who has DNS access?
3. **Industry list** — confirm the 8 niches from your screenshot are the target list (recruiting, men's health, men's coaching, MCA, marketing agency, AI agency, HVAC, solar)?
4. **The skill link** — what is `soulful-quill-nnww.here.now` and where does it get used?
5. **Notion** — which workspace/page should the tracking live in?
6. **Governance status** — is the Overdeliver company already provisioned in your instance (Architect run, API keys set), or am I doing the full setup from its `DEPLOYMENT.md`?

---

## 9. Bonus — starter name ideas for the industry newsletters

(For brainstorming with Justin — his style: playful, industry-insider puns.)

| Niche | Name candidates |
|---|---|
| Men's health | **The Alpha Mail** (boss's pick) · The Open Mail |
| Recruiting/staffing | **The People Person** (boss's pick) · The Short List |
| Men's coaching | The Inner Circuit · Held Standard |
| MCA (merchant cash advance) | The Daily Advance · Fast Money Memo |
| Marketing agencies | The Retainer · Above the Fold |
| AI agencies | The Build Sheet · Agents & Agencies |
| HVAC | The Vent · Full Blast |
| Solar | The Ray · Peak Sun |

---

*This doc lives at `Newsletter\TASK-BREAKDOWN.md`. Both zips are extracted next to it. Claude keeps project memory across sessions — just open a new chat in this folder and say "newsletter task" to resume.*
