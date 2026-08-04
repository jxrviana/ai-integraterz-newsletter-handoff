# Deliverability Fix Plan — scaleverticalwithai.com via JangoMail

Written 2026-07-24. Every technical claim below is traceable to a source fetched during this research; every URL used is listed in **Sources** at the bottom. Where something could not be verified it is marked explicitly.

Baseline: mail-tester score **3.6/10**. Sending IP `63.143.55.226`, HELO `lsn025-i.jsmtp.net`, From `email@scaleverticalwithai.com`.

---

## The one-paragraph summary

Two separate things are wrong, and neither is about the writing or the design. **First**, the domain's DNS never tells the world that JangoMail is allowed to send email as `scaleverticalwithai.com`. The SPF record currently only authorises Hostinger. So every receiving mail server checks, finds JangoMail is not on the approved list, and marks the message as "probably forged" — that is the single largest chunk of lost points, and it is fixed by adding nine words to one DNS record. **Second**, the newsletter HTML contains one line of text set to `font-size:1px` — the hidden "preview text" line that shows in the inbox next to the subject. Spam filters treat 1-pixel text as the classic trick spammers use to hide keywords, so SpamAssassin fires a rule worth 2.5 points. The fix is to delete `font-size:1px;line-height:1px;` from that one line; the preview text still works, because `display:none` is what actually hides it. Everything else in this document is either confirming the DKIM signature is genuinely switched on, or bringing the account up to the Gmail/Yahoo bulk-sender rules that have been mandatory since February 2024.

---

## Fix 1 — Authorise JangoMail in SPF

**Ranked first: this is the largest single block of lost points (mail-tester's −3 authentication failure plus −0.972 `SPF_SOFTFAIL`), and it also gates the Gmail/Yahoo bulk-sender requirements.**

### What's wrong

The published record is:

```
v=spf1 include:_spf.mail.hostinger.com ~all
```

Live lookup confirms `_spf.mail.hostinger.com` resolves to `v=spf1 include:relay.mail.hostinger.com include:relay.mailchannels.net ~all` — Hostinger and MailChannels IP ranges only. JangoMail's sending IP `63.143.55.226` is nowhere in that tree, so SPF returns **softfail**, which is what SpamAssassin's `SPF_SOFTFAIL` reports: *"SPF: sender does not match SPF record (softfail)"* (`rules/25_spf.cf`).

Live lookup also confirms the correct fix: `jangomail.com` publishes

```
v=spf1 include:spf-a.jangomail.com include:spf-b.jangomail.com include:spf-c.jangomail.com include:spf-d.jangomail.com -all
```

and `spf-c.jangomail.com` contains `ip4:63.143.55.128/25`, which covers `63.143.55.226`. So `include:jangomail.com` authorises the observed sending IP. JangoMail's own SPF page instructs customers with an existing record to *"edit your existing record and add 'include:jangomail.com'"*.

**Do not use mail-tester's suggestion of `ip4:63.143.55.226`.** JangoMail sends from at least four separate IP blocks (spf-a through spf-d, dozens of ranges). Hard-coding one IP will pass today's test and softfail the moment JangoMail routes a send through a different pool.

### The exact fix

Replace the TXT record value with:

```
v=spf1 include:_spf.mail.hostinger.com include:jangomail.com ~all
```

Three notes on that exact string:

1. **Only one SPF record may exist on the domain.** Do not add a second TXT record — merge into the existing one, as above.
2. **Do not add `a mx`,** even though JangoMail's template shows `v=spf1 include:jangomail.com a mx -all`. Counting DNS-querying mechanisms per RFC 7208 §4.6.4 (limit: 10, exceeding it returns `permerror`), the merged record above costs **8 lookups**: `_spf.mail.hostinger.com`, `relay.mail.hostinger.com`, `relay.mailchannels.net`, `jangomail.com`, `spf-a`, `spf-b`, `spf-c`, `spf-d`. Adding `a` and `mx` takes it to exactly 10 with zero headroom — one change by Hostinger or JangoMail upstream and the whole record breaks.
3. **Keep `~all` for now.** JangoMail recommends `-all` and notes *"in the eyes of the major mailbox providers ~all and -all will both result in SPF failure."* That is true for the softfail deduction — `~all` vs `-all` does not change whether JangoMail passes, because the `include:jangomail.com` mechanism matches *before* the `all` is reached. Tighten to `-all` only after DMARC reports (Fix 4) confirm nothing else legitimate sends as this domain.

### Who does it

**DNS owner** (whoever controls the `scaleverticalwithai.com` zone — likely Hostinger's DNS panel).

### How to verify it worked

Wait for TTL, then run `nslookup -type=TXT scaleverticalwithai.com` and confirm the new value. Then send a fresh mail-tester: `SPF_SOFTFAIL` must be gone and the authentication section must read `spf=pass`. JangoMail suggests the Kitterman SPF validator for record checking.

**Source:** <https://jangomail.com/spf-records/> · <https://www.rfc-editor.org/rfc/rfc7208.html> · <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/25_spf.cf> · live DNS lookups performed 2026-07-24

---

## Fix 2 — Delete `font-size:1px` from the preheader

**This is the `FONT_INVIS_MSGID` −2.499 deduction. Diagnosis is confirmed, not suspected.**

### What's wrong — and the correction to the working theory

The suspected cause was *"font colour exactly matches background colour."* **That is not the cause.** I read the actual shipped files. All five newsletters (`green-room-issue-1`, `protocol-issue-1`, `people-person-issue-1`, `daily-sun-issue-1`, `bowlegged-mechanic-issue-1`, each at `index.html` line 19) contain:

```html
<div style="display:none;max-height:0;overflow:hidden;mso-hide:all;font-size:1px;line-height:1px;">Plus: …</div>
```

There is **no `color:` declaration in that div at all**. The colour-matches-background theory is refuted by the files themselves.

The real trigger is `font-size:1px`. Here is the rule, pulled verbatim from Apache's own source (`rulesrc/sandbox/jhardin/20_misc_testing.cf`, lines 2601–2651):

```
rawbody   __FONT_INVIS   /<(?!style)[a-z]+\s[^>]{1,80}(?:font(?:-size)?\s*:\s*(?:0*[01](?:\.\d+)?(?:px|pt|Q|vw|vh|vmin)|0+(?:\.\d+)?(?:cm|mm|pc|ch|rem|lh|vmax|%)|0+(?:\.0\d*)(?:em|ex|in))(?:\s[a-z]|\s*[;'])|['"\s;]color\s*:\s*transparent\s*[;'])[^>]{0,80}>[a-z0-9]/i
tflags    __FONT_INVIS   multiple maxhits=11

meta      __FONT_INVIS_MSGID   __FONT_INVIS && __MSGID_OK_HOST
meta      FONT_INVIS_MSGID     __FONT_INVIS_MSGID && !__RCD_RDNS_MX_MESSY && !__RCD_RDNS_MX && !__HAS_ERRORS_TO && !__RCD_RDNS_MAIL && !__MAIL_LINK && !__HDR_RCVD_AMAZON && !__MIME_QP && !__HAS_CAMPAIGNID && !__HAS_THREAD_INDEX && !__RCD_RDNS_MTA
describe  FONT_INVIS_MSGID     Invisible text + suspicious message ID
score     FONT_INVIS_MSGID     2.500	# limit
```

**`__FONT_INVIS` triggers on exactly two things, and nothing else:**

| Technique | Trips `__FONT_INVIS`? |
|---|---|
| `font-size` (or `font:`) with a value starting `0` or `1` in `px pt Q vw vh vmin`, or near-zero in `cm mm pc ch rem lh vmax % em ex in` | **YES** |
| `color:transparent` | **YES** |
| `display:none` | No |
| `opacity:0` | No |
| `visibility:hidden` | No |
| `max-height:0; overflow:hidden` | No |
| font colour equal to background colour | No — that is a *different* rule, see below |

Walking our div through the regex: `<div` + space → `[^>]{1,80}` consumes `style="display:none;max-height:0;overflow:hidden;mso-hide:all;` (62 chars, under the 80 limit) → `font-size:1px` matches `font(?:-size)?\s*:\s*0*[01]…px` → the following `;` matches `\s*[;']` → `[^>]{0,80}` consumes `line-height:1px;"` (17 chars) → `>` → `[a-z0-9]` matches the `P` of "Plus". **Confirmed match.** Each file contains exactly one such declaration, so `__FONT_INVIS` scores exactly one hit — which is all the meta needs.

### On the `MSGID` half of the meta — the important finding

`__MSGID_OK_HOST` is defined in `rules/20_head_tests.cf` as:

```
header __MSGID_OK_HOST		Message-ID =~ /\@(?:\D{2,}|(?:\d{1,3}\.){3}\d{1,3})>/
```

That matches any Message-ID whose `@host>` portion contains two or more consecutive non-digit characters — i.e. **essentially every well-formed Message-ID ending in a normal domain name.** Despite the rule's `describe` line saying *"Invisible text + suspicious message ID"*, the MSGID half is not a suspicion test at all; it is a near-universal condition that any ESP's Message-ID satisfies. It is **not something a sender can usefully control**, and JangoMail's Message-ID is not the problem.

**Because the meta uses `&&`, removing the `__FONT_INVIS` half defeats the entire rule.** There is no way to defeat it from the MSGID side, and no need to try.

### The bonus: six other landmines disarmed

`__FONT_INVIS` feeds a whole family of published rules in the same file. Every one of them is disarmed by the same one-line edit:

| Rule | Score | Fires when |
|---|---|---|
| `FONT_INVIS_MSGID` | 2.500 | + normal Message-ID (**currently firing**) |
| `FONT_INVIS_POSTEXTRAS` | 3.500 | + a URI matching `__AC_POST_EXTRAS` |
| `FONT_INVIS_DIRECT` | 3.500 | + direct-to-MX delivery |
| `FONT_INVIS_DOTGOV` | 3.500 | + a `.gov` URI |
| `FONT_INVIS_LONG_LINE` | 3.000 | + long lines in the source |
| `FONT_INVIS_HTML_NOHTML` | 3.000 | + malformed HTML |
| `FONT_INVIS_NORDNS` | 2.500 | + no reverse DNS |
| `HTML_TEXT_INVISIBLE_FONT` | 2.000 | + more than 2 invisible-font hits |

Right now only one of these fires because the other conditions happen not to be met. That is luck, not safety.

### The exact fix

In each of the five `index.html` files, **line 19**, change:

```html
<div style="display:none;max-height:0;overflow:hidden;mso-hide:all;font-size:1px;line-height:1px;">Plus: …</div>
```

to:

```html
<div style="display:none;max-height:0px;overflow:hidden;mso-hide:all;">Plus: …</div>
```

Two properties removed: `font-size:1px` and `line-height:1px`. Nothing else changes. `line-height` is not matched by the rule (the regex requires the property to be `font` or `font-size`), but it is pointless without `font-size` and is removed for cleanliness.

### Who does it

**Us** — it is our HTML, edited before the file goes into JangoMail.

### How to verify it worked

`grep -i "font-size:1px" *.html` returns nothing. Then re-run mail-tester: `FONT_INVIS_MSGID` must disappear from the rule list entirely. Also open the message in Gmail on desktop and mobile and confirm the preview text still appears next to the subject line and does **not** appear inside the message body.

**Source:** <https://svn.apache.org/repos/asf/spamassassin/trunk/rulesrc/sandbox/jhardin/20_misc_testing.cf> · <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/20_head_tests.cf> · <https://apache.googlesource.com/spamassassin/+/4cfb271eb8257689e26b2d1ed122ff19996ea4c9%5E!/> · <https://apache.googlesource.com/spamassassin/+/ac9838c8299a819edb1a6559b7bbc0eaaa04c95a%5E!/>

---

## Fix 2b — The recommended preheader snippet, and why

This is the recommendation asked for under research task B, evidence-tested against the four candidate techniques.

### Use this

```html
<div style="display:none;max-height:0px;overflow:hidden;mso-hide:all;">Your preview text goes here.</div>
```

### Why each candidate passed or failed

| Candidate | Verdict | Evidence |
|---|---|---|
| `display:none` alone, no colour, no font-size | **Safe — recommended** | Not matched by `__FONT_INVIS`. Litmus's own preview-text guide gives exactly `<div style="display:none;">Your preview text goes here</div>` as the working snippet. |
| `opacity:0` | Not matched by `__FONT_INVIS` | The regex covers only near-zero font sizes and `color:transparent`. **However** I found no evidence that `opacity:0` reliably hides preheaders across clients, and it is not what Litmus recommends — so "not flagged" is not the same as "use it". |
| `max-height:0; overflow:hidden` | Safe, and worth keeping alongside `display:none` | Not matched by any invisible-text rule I examined. It is the standard belt-and-braces fallback for clients that ignore `display:none`. |
| `font-size:1px` / `font-size:0` | **Unsafe — this is the actual bug** | Matched by `__FONT_INVIS` (see Fix 2). Corroborated in the wild: an MJML issue records a developer being told by *"a large email marketing company"* in a code review *"to remove all references to `font-size:0px` because it was a SPAM trigger."* |
| `color:transparent` | **Unsafe** | Explicitly matched by the second branch of the `__FONT_INVIS` regex. |
| Zero-width-space / `&zwnj;` / `&#847;` padding | **Not recommended** | This is the widely-copied "Litmus preheader space hack" used to stop body copy leaking into the preview. It is not matched by `__FONT_INVIS`, but SpamAssassin ships a separate `TVD_SPACE_RATIO` family and I did not verify how long runs of invisible entities score. Given the newsletter already has good preview text, the padding buys nothing and adds unverified risk. |
| Font colour == background colour | Low risk, but avoid anyway | This is `HTML_FONT_LOW_CONTRAST` (`eval:html_test('font_low_contrast')`, *"HTML font color similar or identical to background"*), **not** `__FONT_INVIS`. Its published scores are `0.713 0.001 0.786 0.001` — in the configuration mail-tester appears to use (see note below) it is worth 0.001, i.e. nothing. Our files don't do this anyway. |

**One structural warning.** `display:none` *is* caught by a sibling sub-rule, `__STY_INVIS`:

```
rawbody __STY_INVIS  /\bstyle\s*=\s*"[^">]{0,80}(?:(?<!-)visibility\s*:\s*hidden\s*|display\s*:\s*none\s*)[;"!]/i
tflags  __STY_INVIS  multiple maxhits=6
```

A single hidden div gives one hit, which is harmless: the scored rules built on it need `__STY_INVIS_MANY` (more than 5 hits, `HTML_TEXT_INVISIBLE_STYLE`, 3.500) or extra conditions we don't meet (`STY_INVIS_DIRECT`, 2.500, needs direct-to-MX delivery and no unsubscribe link — we relay through JangoMail and we have an unsubscribe link). **The practical rule: exactly one hidden element per email.** Do not start hiding spacer rows, tracking divs, or alternate content with `display:none`. Current files have exactly one — keep it that way.

*Note on mail-tester's configuration:* SpamAssassin publishes four scores per rule (no-net/no-Bayes, net/no-Bayes, no-net/Bayes, net/Bayes). mail-tester reported `SPF_SOFTFAIL` at 0.972 and `SPF_HELO_NONE` at 0.001, which match the **second** column of `50_scores.cf` exactly (`score SPF_SOFTFAIL 0 0.972 0 0.665`, `score SPF_HELO_NONE 0.001`). **Inference, not documentation:** mail-tester runs with network tests on and Bayes off. I use that assumption when quoting which score column applies.

**Source:** <https://www.litmus.com/blog/the-ultimate-guide-to-preview-text-support> · <https://github.com/mjmlio/mjml/issues/1045> · <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/20_html_tests.cf> · <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/50_scores.cf>

---

## Fix 3 — Confirm DKIM is actually signing (not just that the DNS exists)

### What's wrong

The `jm._domainkey` CNAME → `jm._domainkey.jmsend.com` exists and resolves. **That proves the DNS half is done. It does not prove JangoMail is signing.** In JangoMail the domain key must be separately *enabled* in the account after DNS propagates — their setup flow is: create the domain key, publish the DNS, then click Enable, at which point JangoMail verifies the record and turns signing on.

This matters more than it looks, because of a change in the DMARC standard. RFC 9989 (DMARCbis, published May 2026, obsoletes RFC 7489) specifies that **DMARC's SPF check uses the `MAIL FROM` domain only, with no fallback to HELO.** If JangoMail sets a bounce/Return-Path domain of its own on your sends, SPF will pass but will **not align** with `scaleverticalwithai.com`, and DKIM alignment becomes the only thing carrying DMARC.

*Inference, not documentation:* the fact that mail-tester reported `SPF_SOFTFAIL` **against our record** (rather than a clean pass on a jangomail.com bounce domain), while separately reporting `SPF_HELO_NONE` for the HELO check, indicates the `MAIL FROM` domain currently **is** `scaleverticalwithai.com`. If that holds, Fix 1 delivers both SPF pass *and* SPF alignment. Confirm it from the headers rather than trusting the inference.

### The exact fix

1. In JangoMail: **Settings → Email Settings → DKIM**, confirm the domain shows as enabled (not merely created). If there is an Enable action available, click it.
2. Confirm the signature's `d=` domain is `scaleverticalwithai.com` and **not** `jmsend.com` or `jangomail.com`. Only a `d=` on your own domain produces DKIM alignment for DMARC.

### Who does it

**Us, inside the JangoMail account** — no DNS change needed, the CNAME is already correct.

### How to verify it worked

Send to mail-tester or to a Gmail address, open the raw headers, and check:

- `Authentication-Results:` contains `dkim=pass`
- the `DKIM-Signature:` header contains `d=scaleverticalwithai.com; s=jm`
- `Return-Path:` — note the domain, and whether it matches the From domain

**Source:** <https://knowledge.ondmarc.redsift.com/en/articles/1464266-configure-spf-and-dkim-with-jangomail> · <https://www.rfc-editor.org/rfc/rfc9989.html> · JangoMail's own DKIM help articles at `support.jangomail.com` returned **HTTP 403 to automated fetching**, so their step-by-step is reported here from JangoMail's public search-indexed summaries and a third-party integration guide, not from a page I was able to read in full — see *Open questions*.

---

## Fix 4 — DMARC: add reporting now, enforce later

### What's wrong

Current record is `v=DMARC1; p=none` with **no `rua=`**. That is the worst of both worlds: no protection *and* no visibility. `p=none` means nothing is enforced, and without `rua=` you receive none of the aggregate reports that tell you whether SPF and DKIM are aligning. You are flying blind on the exact question you need answered before you can safely enforce.

### The exact fix — the record to publish today

```
v=DMARC1; p=none; rua=mailto:dmarc@scaleverticalwithai.com
```

Google explicitly warns against pointing `rua` at a personal address: *"We don't recommend using your own email address. Instead, consider using a dedicated mailbox, a group, or a third-party service."* Create `dmarc@scaleverticalwithai.com` as a dedicated mailbox, or point it at a DMARC reporting service.

**Do not include `pct=`.** This is a recent change and most online guides are stale. RFC 9989 (May 2026) removed the `pct` tag outright — it contains an appendix titled *"Removal of the 'pct' Tag"* and the tag no longer appears in the tag registry. dmarc.org's own summary of DMARCbis lists *"Several tags deprecated: pct=, rf=, ri="*. Any guide telling you to ramp `pct=25` → `50` → `100` is written against the obsoleted RFC 7489.

### The safe progression

| Stage | Record | Move on when |
|---|---|---|
| **Now** | `v=DMARC1; p=none; rua=mailto:dmarc@scaleverticalwithai.com` | You have 2–4 weeks of reports and every legitimate sending source (JangoMail, Hostinger webmail, any form/CRM) shows SPF *or* DKIM aligned |
| **Next** | `v=DMARC1; p=quarantine; rua=mailto:dmarc@scaleverticalwithai.com` | Reports show no legitimate mail failing for 2–4 weeks |
| **Optional intermediate** | add `t=y` to the quarantine record | RFC 9989 defines `t=y` as requesting *that the policy not actually be applied* — the standards-track replacement for the old staged rollout. Use it if you want a quarantine record on file without the enforcement effect yet, then remove it |
| **Finally** | `v=DMARC1; p=reject; rua=mailto:dmarc@scaleverticalwithai.com` | Stable for a month at quarantine |

Google's guidance is the same shape: start at `p=none`, *"As you learn how messages from your domain are authenticated by receiving servers, update your policy"*, progressing none → quarantine → reject. dmarc.org: *"Modify your DMARC policy flags from 'none' to 'quarantine' to 'reject' as you gain experience."*

**Do not jump to `p=reject` before Fix 1 and Fix 3 are both verified passing.** With SPF not authorising JangoMail, `p=reject` would bounce your own newsletter.

### Who does it

**DNS owner.**

### How to verify it worked

`nslookup -type=TXT _dmarc.scaleverticalwithai.com`. Then wait 24–48h and confirm aggregate report XML starts arriving at the `rua` mailbox.

**Source:** <https://www.rfc-editor.org/rfc/rfc9989.html> · <https://dmarc.org/2025/12/summary-of-changes-in-dmarcbis/> · <https://dmarc.org/overview/> · <https://knowledge.workspace.google.com/admin/security/set-up-dmarc>

---

## Fix 5 — One-click unsubscribe (RFC 8058) — the biggest open risk

### What's wrong

Gmail requires, for senders of 5,000+ messages/day to Gmail accounts: *"Marketing messages and subscribed messages must support one-click unsubscribe, and include a clearly visible unsubscribe link in the message body"*, implemented with **both** headers:

```
List-Unsubscribe-Post: List-Unsubscribe=One-Click
List-Unsubscribe: <https://[URL]>
```

Yahoo: *"Implement a functioning list-unsubscribe header, which supports one-click unsubscribe for marketing and subscribed messages"* and *"The Post (RFC 8058) method is highly recommended."*

**What JangoMail documents it does:** the List-Unsubscribe feature is *"automatically enabled by default"* for broadcast and transactional sending, inserting *"A URL that will unsubscribe the user when visited"* and *"A mailto address"* — explicitly described as **RFC 2369**. Their published example shows the two-value form:

```
<https://track.yourdomain.com/u.z?j=XXXXXXXXXX&m=...>, <mailto:username@jangomail.com?Subject=Unsubscribe>
```

**What JangoMail does not document anywhere I could find:** any mention of `List-Unsubscribe-Post`, RFC 8058, or one-click. RFC 2369 gives you the header; RFC 8058 gives you *one-click*, and they are not the same requirement.

**I could not verify whether JangoMail emits `List-Unsubscribe-Post`.** Do not assume it does.

### The exact fix

1. Send a test to a Gmail address you control. View → Show original. Search the raw headers for `List-Unsubscribe-Post`.
2. **If present** — nothing to do; confirm the URL is `https://` (a `mailto:`-only header does not satisfy Gmail/Yahoo one-click).
3. **If absent** — open a ticket with JangoMail support asking specifically: *"Does JangoMail add the `List-Unsubscribe-Post: List-Unsubscribe=One-Click` header per RFC 8058, and if so how is it enabled on my account?"* If the answer is no, this is a blocker for sending at bulk volume to Gmail and Yahoo and needs escalating before the list grows past 5,000/day.
4. Independently of the header: keep the visible unsubscribe link in the body. All five newsletter files already contain unsubscribe text (2 occurrences each) — verified.

The account-level toggle, if you need it, is **Settings → Reply Management → Unsubscribe Request Handling → "Include List-Unsubscribe header"** checkbox.

### Who does it

**The ESP** decides whether the header exists; **us** to test and escalate.

### How to verify it worked

Raw headers of a Gmail-delivered test show both `List-Unsubscribe:` with an `https://` URI and `List-Unsubscribe-Post: List-Unsubscribe=One-Click`, and Gmail renders a native "Unsubscribe" link beside the sender name.

**Source:** <https://support.google.com/a/answer/81126> · <https://senders.yahooinc.com/best-practices/> · <https://jangomail.com/email-deliverability-101-list-unsubscribe-header/>

---

## Fix 6 — Turn on the plain-text part

### What's wrong

An HTML-only message fires `MIME_HTML_ONLY` (*"Message only has text/html MIME parts"*), scored `0.1`. Small, but it is free to fix and HTML-only is a soft reputation signal beyond SpamAssassin.

### The exact fix

In the JangoMail message editor, open the **second tab labelled "Plain Text"** and choose one of the two documented options:

- **"Generate now based on HTML message"** — creates it immediately and lets you edit it (recommended: strip duplicated tracking links).
- **"Generate automatically at send time"** — regenerates from the HTML right before the message is processed.

JangoMail's own guidance: *"Always generate a plain text version of your email."*

**One trap to avoid.** Do not hand-write a plain-text part that says something different from the HTML. SpamAssassin ships `MPART_ALT_DIFF` (*"HTML and text parts are different"*, `eval:multipart_alternative_difference('99','100')`) scored `2.246 0.724 0.595 0.790` and `MPART_ALT_DIFF_COUNT` scored `2.799 1.483 1.199 1.112`. A mismatched plain-text part can cost you more than having none. Generating from the HTML keeps them aligned.

### Who does it

**Us, in the JangoMail editor**, per issue.

### How to verify it worked

mail-tester's message-structure section shows both `text/plain` and `text/html` parts, and `MIME_HTML_ONLY` disappears from the rule list.

**Source:** <https://jangomail.com/plain-text-emails/> · <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/20_body_tests.cf> · <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/50_scores.cf>

---

## Fix 7 — Other deductions worth pre-empting (image-heavy HTML to cold recipients)

Checked against the current newsletters; most of these are already fine, which is worth knowing so nobody "fixes" a non-problem.

**Text-to-image ratio — currently safe, protect it.** `HTML_IMAGE_ONLY_04` through `_32` fire on *"HTML: images with 0–400 … 2800–3200 bytes of words"* respectively (`eval:html_image_only('0000','0400')` etc.), scoring up to 1.781 in the relevant column. They only fire when the message has images **and** less than ~3,200 bytes of actual words. Measured: the current issues carry roughly **12,000–14,000 bytes** of visible text against 8 images. Comfortably clear. The rule to hold: **never ship an issue with under ~3,200 bytes (roughly 500+ words) of real text.** A short, image-led issue would trip this. The separate `HTML_IMAGE_RATIO_02/04/06/08` (*"HTML has a low ratio of text to image area"*) rules are all scored `0.001` — effectively free, ignore them.

**Missing headers.** `MISSING_DATE` scores `2.739 1.396 1.800 1.360` and `MISSING_MID` `0.552 0.140 1.199 0.497`. JangoMail supplies both; just never strip or override them with custom headers.

**URL shorteners.** SpamAssassin 4.0 ships a dedicated `25_url_shortener.cf` with a `DecodeShortURLs` plugin that expands shorteners and fires `URL_SHORTENER_CHAINED` (*"Message contains shortened URL chained to other shorteners"*) among others. Use full destination URLs on your own domain; never bit.ly-style links in a cold-audience newsletter, and never chain one shortener into another.

**Link protocol consistency.** `HTTPS_HTTP_MISMATCH` scores `0.1` — anchor text advertising `https://` while the `href` points at `http://`. Keep every link `https://` in both places.

**Subject line.** `SUBJ_ALL_CAPS` scores a flat `0.5`. Avoid all-caps subjects. I did **not** find a verified SpamAssassin rule for exclamation marks or specific "spam words" in subjects at a score worth worrying about, and I am not going to invent one.

**Domain and IP reputation / domain age.** `NO_DNS_FOR_FROM` scores `0.379` in the relevant column — the From domain must resolve, which yours does. On *domain age* specifically: I **could not verify** a current SpamAssassin rule that scores newly-registered domains at a meaningful weight, so I am not claiming one. What is documented is that Gmail and Yahoo both judge you on **spam complaint rate**, which is behaviour, not age — see the checklist below.

**Cold recipients — the honest warning.** Nothing in this document makes cold-list sending safe. Gmail's threshold is a hard ceiling: *"Keep spam rates reported in Postmaster Tools below 0.10%"* recommended, and *"below 0.3%"* as the never-exceed. A cold list blows through 0.3% easily, and no amount of SPF/DKIM correctness compensates. Fix the technical layer first, then warm up volume gradually on people who actually asked for this.

**Source:** <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/20_html_tests.cf> · <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/50_scores.cf> · <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/25_url_shortener.cf> · <https://support.google.com/a/answer/81126>

---

## The DNS records to paste

Two records. Both are **TXT**. Both go in the DNS zone for `scaleverticalwithai.com`.

### Record 1 — SPF (EDIT the existing record, do not add a second one)

| Field | Value |
|---|---|
| Type | `TXT` |
| Host / Name | `@` (or `scaleverticalwithai.com` — whichever your DNS panel uses for the root) |
| TTL | `3600` (or leave default) |
| Value | `v=spf1 include:_spf.mail.hostinger.com include:jangomail.com ~all` |

```
v=spf1 include:_spf.mail.hostinger.com include:jangomail.com ~all
```

⚠️ There must be **exactly one** `v=spf1` TXT record on the root. If you add a second, both become invalid.

### Record 2 — DMARC (EDIT the existing record)

| Field | Value |
|---|---|
| Type | `TXT` |
| Host / Name | `_dmarc` (some panels want the full `_dmarc.scaleverticalwithai.com`) |
| TTL | `3600` (or leave default) |
| Value | `v=DMARC1; p=none; rua=mailto:dmarc@scaleverticalwithai.com` |

```
v=DMARC1; p=none; rua=mailto:dmarc@scaleverticalwithai.com
```

⚠️ Create the `dmarc@scaleverticalwithai.com` mailbox (or a forwarder) **before** publishing this, or the reports bounce.

### Record 3 — DKIM: NO CHANGE NEEDED

Already correct and resolving. Listed here only so nobody "helpfully" edits it.

| Field | Value |
|---|---|
| Type | `CNAME` |
| Host / Name | `jm._domainkey` |
| Value | `jm._domainkey.jmsend.com` |

**Leave this alone.** The remaining DKIM work (Fix 3) is inside the JangoMail account, not in DNS.

### Nothing to do about `SPF_HELO_NONE`

The −0.001 `SPF_HELO_NONE` deduction is *"SPF: HELO does not publish an SPF Record"* — it refers to JangoMail's own HELO hostname `lsn025-i.jsmtp.net`, on a domain we do not own and cannot publish records for. It is worth `0.001`. **Ignore it.** It cannot be fixed from our side and it is not worth a support ticket.

---

## Gmail and Yahoo bulk sender checklist

Requirements in force since 1 February 2024. Status assessed **after** Fixes 1–6 are applied; the "now" column is today's state.

| Requirement | Gmail | Yahoo | Now | After fixes | What's still needed |
|---|---|---|---|---|---|
| SPF published and passing | Required (bulk: SPF **and** DKIM) | *"Implement both SPF & DKIM"* | ❌ FAIL — softfail | ✅ | Fix 1 |
| DKIM published and signing | Required for bulk | Required for bulk; min. 1024-bit key | ⚠️ UNKNOWN — DNS exists, signing unconfirmed | ✅ | Fix 3 — verify `dkim=pass` in headers |
| DMARC record published, min. `p=none` | *"Your DMARC enforcement policy can be set to none"* | *"Publish a valid DMARC policy with at least p=none - DMARC must pass"* | ✅ PASS (bare minimum) | ✅ | Add `rua=` for visibility (Fix 4) |
| DMARC alignment — From domain aligns with SPF **or** DKIM domain | Required for bulk | *"Ensure the domain in the From: header is aligned with either the SPF domain or the DKIM domain"* | ❌ FAIL — neither currently aligns | ✅ expected | Fixes 1 + 3; confirm from headers |
| One-click unsubscribe: `List-Unsubscribe` + `List-Unsubscribe-Post: List-Unsubscribe=One-Click` | Required for bulk | *"The Post (RFC 8058) method is highly recommended"* | ⚠️ **UNKNOWN — likely FAIL** | ⚠️ | **Fix 5 — the biggest open risk.** JangoMail documents RFC 2369 only |
| Visible unsubscribe link in body | *"include a clearly visible unsubscribe link in the message body"* | *"Have a clearly visible unsubscribe link in the email body"* | ✅ PASS — present in all 5 issues | ✅ | — |
| Honour unsubscribes promptly | Not stated on the page I fetched | *"Honor unsubscribes within 2 days"* | ⚠️ UNVERIFIED | — | Confirm JangoMail's unsubscribe processing SLA |
| Spam complaint rate | *"below 0.10%"* recommended, *"below 0.3%"* never-exceed | *"Keep your spam rate below 0.3%"* | ⚠️ UNMEASURED | — | **Register the domain in Google Postmaster Tools** — you cannot manage what you can't see |
| Valid forward and reverse DNS (PTR) on sending IP | Required — PTR must resolve to a hostname with a matching A/AAAA | *"Have a valid forward and reverse DNS record for your sending IPs"*, *"meaningful, non-generic"* | ✅ likely PASS — ESP's responsibility; `63.143.55.226` → `lsn025-i.jsmtp.net` | ✅ | JangoMail's job, not ours |
| TLS on transmission | *"Use a TLS connection for transmitting email"* | Not stated on the page I fetched | ✅ likely PASS — ESP's responsibility | ✅ | — |
| RFC 5322 message format | *"Format messages according to the Internet Message Format standard, RFC 5322"* | — | ✅ likely PASS | ✅ | — |
| Don't impersonate Gmail in From | *"Gmail will begin using a DMARC quarantine enforcement policy"* | — | ✅ PASS — sending as own domain | ✅ | — |

**Threshold note:** the additional bulk requirements apply to senders of *"more than 5,000 messages per day to Gmail accounts."* Google's page does not define how that volume is averaged. Even below the threshold, everything above is good practice and most of it is required of all senders anyway.

**Source:** <https://support.google.com/a/answer/81126> · <https://senders.yahooinc.com/best-practices/>

---

## Verification steps

Run in this order. Do not skip ahead — later checks are meaningless if earlier ones fail.

**Step 1 — Before any DNS change: record the baseline.**
Save the current mail-tester report URL and the full raw headers of the test message. You need the `Return-Path:` and `Authentication-Results:` lines to prove what changed.

**Step 2 — Edit the HTML (no waiting required).**
```
grep -i "font-size:1px" */index.html
```
Must return nothing across all five issues. Also confirm exactly one `display:none` per file.

**Step 3 — Publish the two DNS records.** Then wait for TTL (up to 1 hour typically; JangoMail warns DNS changes *"may take up to 48 hours"*).

**Step 4 — Verify DNS independently of the ESP.**
```
nslookup -type=TXT scaleverticalwithai.com
nslookup -type=TXT _dmarc.scaleverticalwithai.com
nslookup -type=CNAME jm._domainkey.scaleverticalwithai.com
```
Expect: one SPF record containing `include:jangomail.com`; the DMARC record containing `rua=`; the DKIM CNAME resolving to `jm._domainkey.jmsend.com`.

**Step 5 — Confirm the SPF record still evaluates.** Run it through an SPF validator (JangoMail suggests Kitterman) and confirm no `permerror` and a DNS-lookup count of **8** or fewer.

**Step 6 — Enable/confirm DKIM in the JangoMail UI.** Settings → Email Settings → DKIM. Domain must show as enabled.

**Step 7 — Send a real test to a Gmail address you control.** Show original, and confirm all four lines:
- `spf=pass` with the domain `scaleverticalwithai.com`
- `dkim=pass` with `header.d=scaleverticalwithai.com`
- `dmarc=pass`
- `List-Unsubscribe-Post: List-Unsubscribe=One-Click` present (this is the Fix 5 decision point)

**Step 8 — Re-run mail-tester.** Expect these three gone: `FONT_INVIS_MSGID`, `SPF_SOFTFAIL`, and the −3 authentication penalty. Expect `SPF_HELO_NONE` (−0.001) to **remain** — that is correct and unfixable, see above.

**Step 9 — Enable the plain-text part** and re-run mail-tester once more; `MIME_HTML_ONLY` should be gone and `MPART_ALT_DIFF` should **not** have appeared.

**Step 10 — Register the domain in Google Postmaster Tools** and let data accumulate before any volume increase.

**Step 11 — Two to four weeks later**, read the DMARC aggregate reports before moving `p=none` → `p=quarantine`.

---

## Open questions / could not verify

1. **Does JangoMail emit `List-Unsubscribe-Post: List-Unsubscribe=One-Click`?** Their public documentation describes RFC 2369 (URL + mailto) only, with no mention of RFC 8058 or one-click anywhere I could find. Their help centre at `support.jangomail.com` returns **HTTP 403 to automated fetching**, so I could not read the full List-Unsubscribe article — only JangoMail's own blog version of it. **This must be answered from live message headers, then from JangoMail support.** It is the single biggest unresolved compliance risk.

2. **JangoMail's DKIM article could not be read.** `support.jangomail.com/hc/en-us/articles/360039011254-DKIM-Explained` and the SPF article both returned 403. Details on the DKIM setup flow here come from JangoMail's search-indexed summaries plus Red Sift's OnDMARC integration guide. There is also an apparent discrepancy between JangoMail documentation describing a **TXT** DKIM record and your live DNS using a **CNAME** delegation to `jmsend.com`. The CNAME resolves, so it works; I could not confirm from JangoMail's own docs which method is current. **Not a blocker** — the verification that matters is `dkim=pass` in real headers.

3. **What `Return-Path` / `MAIL FROM` domain JangoMail sets on your sends.** This determines SPF *alignment* for DMARC, which matters more under RFC 9989 (no HELO fallback). My inference from the `SPF_SOFTFAIL`-on-our-domain result is that it is already `scaleverticalwithai.com`, but that is inference and must be confirmed from the raw headers.

4. **JangoMail's unsubscribe processing SLA.** Yahoo requires honouring unsubscribes *"within 2 days."* I found no JangoMail statement on their processing time.

5. **The exact published score of `FONT_INVIS_MSGID`.** The rule source sets `score FONT_INVIS_MSGID 2.500 # limit`; mail-tester reported 2.499. The published ruleset re-scores rules within that limit, and I did not locate the generated score file. The difference is immaterial.

6. **How many points each fix returns on mail-tester's 10-point scale.** mail-tester does not publish its scoring formula and I did not find documentation for it. I have quoted **SpamAssassin's own rule scores**, which are what the deductions are derived from — but I am not going to translate those into "this gets you to 9/10", because no source states that. Re-test and measure.

7. **Whether zero-width-space preheader padding is penalised.** Not matched by `__FONT_INVIS`, but I did not verify how SpamAssassin's `TVD_SPACE_RATIO` family scores long runs of invisible entities. Avoided on precaution, not on evidence.

8. **Domain age as a scored factor.** Could not verify a current SpamAssassin rule that penalises newly-registered domains at a meaningful weight. Claim not made.

---

## Sources

**SpamAssassin rule sources (primary — Apache SVN / Apache git)**
- <https://svn.apache.org/repos/asf/spamassassin/trunk/rulesrc/sandbox/jhardin/20_misc_testing.cf> — `__FONT_INVIS`, `__STY_INVIS`, `__WORD_INVIS`, `FONT_INVIS_MSGID` and the whole FONT_INVIS family with scores
- <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/20_head_tests.cf> — `__MSGID_OK_HOST`, `__MSGID_OK_HEX`, `__MSGID_OK_DIGITS`
- <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/20_html_tests.cf> — `HTML_FONT_LOW_CONTRAST`, `HTML_IMAGE_ONLY_*`, `HTML_IMAGE_RATIO_*`
- <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/20_body_tests.cf> — `MPART_ALT_DIFF`, `MPART_ALT_DIFF_COUNT`
- <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/25_spf.cf> — `SPF_SOFTFAIL`, `SPF_HELO_NONE` definitions and descriptions
- <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/25_url_shortener.cf> — URL shortener rules and the DecodeShortURLs plugin
- <https://svn.apache.org/repos/asf/spamassassin/trunk/rules/50_scores.cf> — published default scores
- <https://apache.googlesource.com/spamassassin/+/4cfb271eb8257689e26b2d1ed122ff19996ea4c9%5E!/> — commit defining `__FONT_INVIS_MSGID` / `FONT_INVIS_MSGID`
- <https://apache.googlesource.com/spamassassin/+/ac9838c8299a819edb1a6559b7bbc0eaaa04c95a%5E!/> — commit tuning the `__FONT_INVIS` regex units
- <https://www.mail-archive.com/users@spamassassin.apache.org/msg111564.html> — SA 4.0 form of the `FONT_INVIS_MSGID` meta with its full exclusion list

**Standards**
- <https://www.rfc-editor.org/rfc/rfc7208.html> — SPF, §4.6.4 the 10 DNS-lookup limit
- <https://www.rfc-editor.org/rfc/rfc9989.html> — DMARCbis; obsoletes RFC 7489, removes `pct`, defines `t=`

**Mailbox provider requirements**
- <https://support.google.com/a/answer/81126> — Google Email sender guidelines
- <https://knowledge.workspace.google.com/admin/security/set-up-dmarc> — Google's DMARC rollout guidance
- <https://senders.yahooinc.com/best-practices/> — Yahoo sender best practices / requirements

**DMARC guidance**
- <https://dmarc.org/overview/> — deployment progression, `rua`/`ruf`
- <https://dmarc.org/2025/12/summary-of-changes-in-dmarcbis/> — deprecated tags in DMARCbis

**JangoMail**
- <https://jangomail.com/spf-records/> — official SPF instructions
- <https://jangomail.com/email-deliverability-101-list-unsubscribe-header/> — List-Unsubscribe behaviour and account setting
- <https://jangomail.com/plain-text-emails/> — plain-text generation options
- <https://knowledge.ondmarc.redsift.com/en/articles/1464266-configure-spf-and-dkim-with-jangomail> — third-party JangoMail SPF/DKIM integration guide
- `https://support.jangomail.com/hc/en-us/articles/200621095-SPF-Record` — **HTTP 403, could not read**
- `https://support.jangomail.com/hc/en-us/articles/360039011254-DKIM-Explained` — **HTTP 403, could not read**
- `https://support.jangomail.com/hc/en-us/articles/360060375694-List-Unsubscribe-Header` — **HTTP 403, could not read**

**Preheader technique**
- <https://www.litmus.com/blog/the-ultimate-guide-to-preview-text-support> — Litmus's recommended hidden preview-text snippet
- <https://github.com/mjmlio/mjml/issues/1045> — real-world report of `font-size:0px` flagged as a spam trigger in an ESP code review

**Live DNS lookups performed 2026-07-24** (`Resolve-DnsName`, including against 8.8.8.8): `scaleverticalwithai.com`, `_spf.mail.hostinger.com`, `relay.mail.hostinger.com`, `relay.mailchannels.net`, `jangomail.com`, `spf-a/b/c/d.jangomail.com`

**Local files inspected:** `green-room-issue-1/index.html`, `protocol-issue-1/index.html`, `people-person-issue-1/index.html`, `daily-sun-issue-1/index.html`, `bowlegged-mechanic-issue-1/index.html` (all line 19)

---

## Sources I deliberately did not rely on

Several high-ranking pages purporting to explain `FONT_INVIS_MSGID` are AI-generated SEO content that describes the rule as testing for a *"suspiciously formatted or inconsistent Message-ID."* Reading the actual rule shows that is wrong — `__MSGID_OK_HOST` matches virtually every well-formed Message-ID. Anything in this document about SpamAssassin comes from the rule source itself.
