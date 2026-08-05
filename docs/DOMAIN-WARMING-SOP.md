# SOP — Buying + Warming Sending Domains
**For Xander · plain English · created 2026-08-05 after the `localaffiliatepro.com` flag.**

## Why this exists
`localaffiliatepro.com` got flagged because we sent ~18.5k on a **brand-new domain with no warmup.** Gmail/Outlook distrust new senders — blast too much too fast and you get spam-filtered or blocklisted. **Warming = slowly building trust so your mail lands in the inbox.**

## Lane check first (read this)
In the huddle Justin said *he* handles deliverability/technical/**domains** and *you* stay on content + ops. **This whole SOP is Justin's lane** — you don't need Spaceship access and shouldn't own domain-buying, DNS auth, or warming unless he explicitly hands a piece to you. Keep it here as **reference** so you understand the system and can pick up a delegated piece if asked. If any of this starts landing on your plate day-to-day, that's the signal to hand it back to Justin.

---

## PART 1 — Buying a domain (🟩 you, on Justin's account)
**Where: Justin's Spaceship account** (the registrar he uses — same place his DNS lives). He said he'd give you access and there's a card on file. **Do NOT buy on your own personal account** — the domain has to live where Justin can set DNS auth + connect the SMTP, or it's a dead purchase.

⚠️ **Confirm with Justin before buying:** *"Am I in your Spaceship account, and what's the budget?"* (He said ~$10–20/day, not $50.)

**Steps (once you're in Spaceship):**
1. Search for a domain — cheap, plain, **brandable, tied to the niche** (e.g. solar → `solaraffiliatedesk.com`). No spammy words, no hyphens/numbers.
2. Prefer **`.com`** (`.co`/`.net` ok). ~$1–12/yr.
3. Buy it (card on file).
4. **Tell Justin the new domain** so he sets up SPF/DKIM/DMARC — **it can't send until he does.**
- Buy a **few at a time.** We rotate them, and some will burn — Justin said that's expected and fine.

## PART 2 — Warming it (🟦 auth first, then 🟩 you run the ramp)
**Step 0 (🟦 Justin):** SPF + DKIM + DMARC on the domain + connect it to the SMTP. **Nothing below happens until this is green.**

Use **both** methods together:

**A. Automated warmup service (easiest — set-and-forget).**
A service auto-sends mail between a network of real inboxes and auto-opens/replies, building the domain's reputation **without touching our cold list** — which is exactly why it's the safe way to warm. Justin referenced **MailReach** (~$25/mo) and **Mailreef** (`mailreef.com` — watch the video he sent; it draws out the IP/domain/server layers). → Connect each new domain's mailbox, let it run **~2–4 weeks.**

**B. Ramped real sends (your newsletters), slow and steady:**
| Day | Volume per domain |
|---|---|
| 1–2 | 20–50 |
| 3–4 | 75–100 |
| 5–7 | 150–300 |
| Week 2 | ramp ~30–50%/day **if metrics are clean** |
| Weeks 3–4 | build toward full volume |

**The rules (Justin was explicit):**
- **Consistency beats bursts.** Steady daily volume. **Never spike** (20k one day, 5k the next → you lose reputation). Pick a number and hold it every day.
- **Cleanest recipients first** — verified, most-likely-to-open.
- **Watch metrics daily:** bounce <1%, complaints <0.1%, and inbox-vs-spam (send yourself a Gmail test + run mail-tester). If any slips → **hold the ramp**, don't advance.
- **Verify the list first** (the edcom verify-hub / verification playbook) so bounces stay under 1%.

## PART 3 — The "always warming" pipeline
Justin wants domains warming **all the time**:
- Keep a **rotating set:** warmed domains carry the send load; 1–2 new domains always warming in the background.
- As a domain ages or burns → retire it, promote a warmed one, start a new one.
- Target **~20k/day total** across warmed domains — held **consistently**.

## The honest tension (worth flagging to Justin)
Textbook warmup says "send to engaged people first" — but our lists are **cold.** That's the real difficulty. The mitigation: (1) the automated seed-network warmup (A) builds reputation *without* the cold list, (2) verify the cold list hard so bounces stay <1%, (3) ramp slowly. This is genuinely Justin's deliverability domain — have him confirm the exact ramp + tooling. **Your job: buy the domains, start the warmup service, run the content at the pace he sets.**
