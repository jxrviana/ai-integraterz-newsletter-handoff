# → SingleBrain: Local Affiliate Pro Issue 001 — fixes (keep as DRAFT, no send)

*(Xander: paste this. Good honest work flagging Pinnacle instead of faking it. A few fixes before this is send-ready. It stays a draft — we haven't decided where Local Affiliate Pro sends yet.)*

## 1. Fix the numbering
The offers currently run 01, 02, 03, **[no 04]**, 05, 06 … 12 — the gap is where Pinnacle Funding was pulled. Renumber the visible offers **sequentially with no gaps** (01 through however many remain).

## 2. Shuffle the order — do NOT put our own offers at the top (important)
Right now positions 1–3 are **Speaker Agent, The Affiliate Machine, ConnectMed** — all our own offers. Leading with all three makes it obvious the newsletter is selling our stuff, which breaks the "neutral curated roundup" feel.
- **Intersperse our offers among the real third-party programs.** Lead with recognizable third-party names (Shopify, HubSpot, etc.), and place ours at mixed positions (e.g., #4, #7, #9) so no cluster of ours sits together and none lead the issue.
- It should read like an unbiased shortlist, not a house ad.

## 3. Pinnacle Funding
Still unverified. Either get its real affiliate URL + terms (from Justin) and include it as a normal entry, or leave it out entirely. Don't leave it in limbo.

## 4. Verify the remaining commission numbers in a real BROWSER
The offers are real, but confirm each commission claim on its live page before this ever sends (monday.com's "up to 100% first year" is already confirmed). Check HubSpot 30%, GetResponse up to 60%, ActiveCampaign 30%, Kinsta $500 + 10%, Hostinger, Shopify, FreshBooks — quote the supporting line for each in the ledger.

## 5. Email-safety
- **Inline the CSS.** It's currently in a `<head><style>` block — Outlook and some clients strip that, breaking the layout. Move styles inline on each element.
- Convert curly quotes and the `©` symbol to ASCII/HTML entities (e.g. `&copy;`, `&rsquo;`).

## 6. Keep it a draft
Do not send or test — we haven't decided the destination for Local Affiliate Pro yet. Deliver the fixed HTML + updated ledger for review. Use the **Local Affiliate Pro skill** (being handed to you) as the standard for this newsletter.
