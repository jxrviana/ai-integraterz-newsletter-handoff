# Bird / Seed Test Newsletter — Draft v1
*Horizontal SMB issue · doubles as deliverability test content · placeholders marked {{LIKE_THIS}} · needs Justin's sender identity before staging*

## Subject line options (pick 1)

1. "The lead you paid for just called your competitor"
2. "Who answers your phone at 7:41pm?"
3. "The five-minute window most businesses miss"
4. "Speed wins jobs your competitors quote cheaper"
5. "A follow-up fix you can set up this week"

**Recommendation:** #2 for the cold blast (short, personal, curiosity with a concrete image); #3 for the JangoMail seed test.

## Preview text

"Most buyers go with whoever answers first. Here's how to be that business."

## Email body (markdown)

Hi {{FIRST_NAME}},

Picture this: it's 2pm on a Tuesday. Someone needs exactly what you sell. They find you, fill out your contact form — and keep scrolling. Two of your competitors are one tab away.

Your form sends you an email. It lands between an invoice and a newsletter. You spot it around 6pm and send a solid, professional reply.

Too late. They booked with the company that texted back in three minutes.

Not because that company is better. They just showed up while the buyer was still sitting there — phone in hand, problem on their mind.

**Here's the lesson most businesses learn the expensive way: leads don't cool off. They get picked up.**

The good news is this is one of the easiest problems in your business to fix. Here's the no-software version you can set up this week:

**1. Set a response rule.** Every inquiry gets an answer within 5 minutes during business hours. Not "when someone gets to it" — a rule, with a name attached to it.

**2. Write one template.** "Hi {name}, got your message about {thing} — I can help. Quick question so I point you right: {one qualifying question}." Thirty seconds to send, and it beats a perfect reply sent four hours later.

**3. Text back every missed call.** A missed call is a lead announcing themselves. "Sorry we missed you — what do you need? We'll call you right back." Even sent manually, it saves jobs.

That's it. No tools, no subscriptions — just a rule, a template, and a habit. It works today.

The hard part is 7:41pm. Weekends. The days everyone's slammed. That's where automation earns its keep: a system that answers every call and every form in under a minute, around the clock, and hands you the conversation already warmed up. That's what we build at {{COMPANY_NAME}} — but start with the manual version above. It's free and it works.

**Want the automated version for your type of business?** Reply with the word **SPEED** and I'll send over exactly how it works — no pitch call, no calendar link, just the details.

Be quick out there.

— {{SENDER_NAME}}
{{SENDER_TITLE}}, {{COMPANY_NAME}}

---
{{COMPANY_NAME}} · {{PHYSICAL_ADDRESS}}
You're receiving this because your business came up in our research. Not for you? One click and we're gone: {{UNSUBSCRIBE_LINK}}

## Plain-text version

Hi {{FIRST_NAME}},

Picture this: it's 2pm on a Tuesday. Someone needs exactly what you sell. They find you, fill out your contact form — and keep scrolling. Two of your competitors are one tab away.

Your form sends you an email. It lands between an invoice and a newsletter. You spot it around 6pm and send a solid, professional reply.

Too late. They booked with the company that texted back in three minutes.

Not because that company is better. They just showed up while the buyer was still sitting there — phone in hand, problem on their mind.

Here's the lesson most businesses learn the expensive way: leads don't cool off. They get picked up.

The good news: this is one of the easiest problems in your business to fix. The no-software version, ready this week:

1. Set a response rule. Every inquiry gets an answer within 5 minutes during business hours. A rule, with a name attached to it.

2. Write one template. "Hi {name}, got your message about {thing} — I can help. Quick question so I point you right: {one qualifying question}." Thirty seconds to send, and it beats a perfect reply sent four hours later.

3. Text back every missed call. "Sorry we missed you — what do you need? We'll call you right back." Even sent manually, it saves jobs.

No tools, no subscriptions — a rule, a template, a habit.

The hard part is 7:41pm. Weekends. Slammed days. That's where automation earns its keep: a system that answers every call and form in under a minute, around the clock. That's what we build at {{COMPANY_NAME}} — but start with the manual version. It's free and it works.

Want the automated version for your type of business? Reply with the word SPEED and I'll send exactly how it works — no pitch call, just the details.

Be quick out there.

— {{SENDER_NAME}}
{{SENDER_TITLE}}, {{COMPANY_NAME}}

{{COMPANY_NAME}} · {{PHYSICAL_ADDRESS}}
You're receiving this because your business came up in our research. Not for you? One click removes you: {{UNSUBSCRIBE_LINK}}

## Notes for staging

- **Must be filled before send (from Justin):** {{SENDER_NAME}}, {{SENDER_TITLE}}, {{COMPANY_NAME}}, {{PHYSICAL_ADDRESS}} (legally required in the footer), and the platform's unsubscribe merge tag for {{UNSUBSCRIBE_LINK}} (Bird and JangoMail each have their own — SingleBrain knows the tags).
- **{{FIRST_NAME}} fallback:** configure the platform default to "there" ("Hi there,") for records with no first name — never send "Hi ,".
- **Zero links by design.** The only CTA is a reply — no links means fewer spam-filter triggers on a cold send, and replies are the strongest positive signal an inbox provider can see. Keep it that way for the test; add links in later issues.
- **No images.** Plain, personal-looking email. Better cold deliverability and it matches the reply-first strategy.
- **The word SPEED is the lead signal** — anyone who replies with it is a hand-raiser. SingleBrain should flag/collect those replies; they route to Justin's service tiers.
- **Seed test first:** send to the seed panel before any real volume (per DELIVERABILITY-TEST-PLAN.md), on JangoMail only after DKIM verifies.
- The "came up in our research" line is honest cold-outreach framing — if Justin's list is actually opted-in from somewhere, swap it for the true source ("you signed up at …"), which always beats generic.
