# General Skill — The Newsletter Pipeline

The end-to-end workflow for producing ONE outbound newsletter. Do one at a time.

1. **RESEARCH** — find real, current (~≤60-day) articles per story; **browser-verify each link loads AND the claim is on the page** (see 01-creation-and-QA). Keep a source ledger with quoted supporting sentences.
2. **DRAFT** — write the copy against 02-format-playbook, in the newsletter's own voice (see its identity skill in `newsletters/`).
3. **IMAGES** — write text-safe Higgsfield prompts, one per slot (05-images). Xander generates the images; you never do.
4. **BUILD** — produce email-safe HTML on the locked design (04-design-front-desk-template).
5. **QA** — run the full 01-creation-and-QA checklist; attach the completed QA report. Fix every BLOCKER before delivering.
6. **LOAD** — into ListMonk as a DRAFT: blank template (ID 8), images via the media API, tracking + bounce on (06-sending-listmonk).
7. **TEST + APPROVE** — a real seed send to prove inbox placement + open/click tracking; Xander reviews the ListMonk preview and approves.
8. **SEND** — only on Xander's explicit go, at a safe rate (06-sending-listmonk).

**Never** deliver an unchanged file as "revised." **Never** fabricate. **Never** auto-send.
