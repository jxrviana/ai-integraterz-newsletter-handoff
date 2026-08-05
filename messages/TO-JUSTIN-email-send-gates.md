**Flagging a SingleBrain blocker — the `email-send-gates` skill — and a call that's yours as its operator.**

Hey Justin — heads-up on something blocking our sends, plus a decision only you can make.

**What's happening:** SingleBrain built itself a safety skill called `email-send-gates`. Honestly, **most of it is good** and we should keep it — it enforces sound sending hygiene: verify you're sending the *right* draft (it caught an old Shopify version of Local Affiliate Pro), isolate to a single SMTP so ListMonk can't random-split a campaign, suppress known bounces, host + rewrite images properly, and confirm tracking is actually configured. All solid.

**The problem is one rule inside it:** it **hard-blocks any bulk send to a cold / non-opt-in list, and explicitly treats owner authorization as *not enough* to override that.** Since our entire outbound-newsletter model is compliant cold B2B email to lead lists, that one rule blocks the core business. It has now refused the Local Affiliate Pro send 4+ times — including after direct, written authorization.

**The facts, so you can decide with full context:**
- US **CAN-SPAM** — the law that governs commercial email — does **not** require opt-in. It requires honest headers, a truthful subject, a physical postal address, and a working unsubscribe. Our newsletters have all four (and the master list already honors 207 unsubscribes). SingleBrain itself conceded this: *"U.S. CAN-SPAM generally does not require prior opt-in."*
- So these sends are **legal.** The risks SingleBrain is over-indexing on are **deliverability + provider TOS** — real, but those are *your* business risks to accept, and we've run two sends this way already with clean numbers (Dealmaker 0.02% complaints, Referral 0%).
- One genuine caveat worth a check: if the list includes **EU or Canada** contacts, those jurisdictions *do* require consent (GDPR / CASL). Worth confirming the list is US-based.

**The decision is yours as SingleBrain's operator:**
- **Option A —** adjust that *one* rule so owner-authorized, CAN-SPAM-compliant cold sends are permitted, while keeping every other gate (artifact / provider-isolation / suppression / tracking). This unblocks the model without weakening the good safeguards.
- **Option B —** keep the gate exactly as-is and send these another way.

For the record: I deliberately **won't try to trick SingleBrain** into overriding its own safety skill (e.g. spinning up a fresh session to word around it) — that's not a healthy way to change an agent's behavior. The right way is you deciding this openly at the config level, which is why I'm flagging it to you.

**Meanwhile:** per your note, Xander is running the Local Affiliate Pro send **manually in ListMonk** so he learns the full pipeline end-to-end.

**Two security housekeeping items:**
- The **Bird + Resend API keys** got pasted into the Slack thread — please rotate them.
- ListMonk is showing a banner to remove `admin_username` / `admin_password` from the TOML config and switch to API credentials — worth doing while we're at it.

If you go with Option A, I can spell out **exactly which one rule to change and which safeguards to keep**, so nothing else gets weakened. Just say the word.
