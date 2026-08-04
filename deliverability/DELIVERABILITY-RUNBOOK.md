# Email Deliverability Runbook — Platform-Agnostic

*2026-07-24. Companion to `DELIVERABILITY-FIX-PLAN.md` (the JangoMail-specific research). Teaches the mechanics, so any new platform can be authenticated and tested in one to two hours. Every claim is carried from that file with its citation, or verified live against the standard; practice rather than documented requirement is tagged **[practice]**.*

**Vocabulary, once.** **ESP** = Email Service Provider (JangoMail, Bird, SmartLead…). **DNS** = where you publish records proving things about your domain. **MAIL FROM domain** (a.k.a. envelope sender, bounce domain, Return-Path) = the hidden address the sending server hands over during the SMTP conversation; where bounces go. **Header From** = the visible address the reader sees. Two different addresses — that difference is the most confusing thing in email.

---

## 1. What actually decides whether mail lands

| Tier | What it is | What it does |
|---|---|---|
| **1. Authentication** | SPF, DKIM, DMARC, reverse DNS | **Table stakes.** Passing gets you *considered*, not delivered. Failing gets you filtered — and Gmail/Yahoo make it mandatory for bulk senders. |
| **2. Reputation** | Complaints, bounces, spam traps, domain and IP sending history | **This decides placement.** Google's documented ceiling is a spam rate below 0.3%, measured from real recipient behaviour. Nothing in your HTML affects it. |
| **3. Engagement** | Opens, replies, deletes-without-reading | Feeds tier 2. No provider publishes a formula, so **[practice]**: send to people who want it, prune the dead. |
| **4. Content** | Layout, links, images, "spam words" | **Matters far less than people think.** Real deductions are *structural*, not vocabulary — a `font-size:1px` div cost us 2.499 SpamAssassin points, while no verified rule penalises exclamation marks or spam words at a score worth worrying about (research file, Fix 7). |

**Never debug content before DNS.** A broken SPF record cannot be fixed by rewriting a subject line.

---

## 2. The four records

### SPF — Sender Policy Framework
**Proves** which servers may send using your domain as the envelope sender. **Without it,** receivers cannot tell your ESP from a forger: softfail or fail, and DMARC loses a leg.

```
Type: TXT   Host: @   Value: v=spf1 include:_spf.mail.hostinger.com include:jangomail.com ~all
```

`include:x` = "also trust whatever `x` publishes," one per sending system. `~all` = softfail (suspicious, usually delivered); `-all` = hardfail. Start at `~all`; tighten once DMARC reports prove nothing legitimate is missing.

**A domain may have exactly ONE `v=spf1` record.** RFC 7208 §3.2: a domain "MUST NOT have multiple records that would cause an authorization check to select more than one record." Two is *worse than none* — permanent error, everything fails.

**Verify:** `nslookup -type=TXT yourdomain.com` → one `v=spf1` line containing your ESP's include.

### DKIM — DomainKeys Identified Mail
**Proves** the message came from your domain unaltered, via a cryptographic signature. **Without it** you lose the only method that survives forwarding (SPF breaks on forward; DKIM does not).

```
Type: CNAME   Host: jm._domainkey   Value: jm._domainkey.jmsend.com
```

Either a TXT record holding a public key, or a CNAME delegating to the ESP so they can rotate it. `jm` is the **selector** — an arbitrary label, so one domain can hold several keys. Publishing is half the job: **signing must also be switched on inside the platform.** DNS existing proves nothing about signing.

**Verify:** a real message's `DKIM-Signature:` shows `d=yourdomain.com; s=<selector>`. If `d=` is the ESP's domain you have DKIM but not *aligned* DKIM.

### DMARC
**Proves** what receivers should do when SPF and DKIM fail to align, and reports who sends as you. **Without it:** no visibility, no protection, and you fail the bulk requirement.

```
Type: TXT   Host: _dmarc   Value: v=DMARC1; p=none; rua=mailto:dmarc@yourdomain.com
```

`p=none` (monitor) → `p=quarantine` → `p=reject`. **Do not use `pct=`** — RFC 9989 (DMARCbis, May 2026) removed it; any guide saying ramp `pct=25→50→100` is written against the obsoleted RFC 7489. Use `t=y` for a policy on file without enforcement.

### Reverse DNS (PTR)
**Proves** the sending IP resolves back to a hostname that resolves forward to the same IP. **Without it** you fail an all-senders Google requirement: "Ensure that sending domains or IPs have valid forward and reverse DNS records, also referred to as PTR records." **Owned by the ESP** — unless you are on a dedicated IP or self-hosting (Listmonk on your own VPS: yours). **Verify:** `nslookup <IP>` returns a hostname; `nslookup <hostname>` returns that same IP.

### Alignment — the concept everyone misses

SPF passing is **not enough**. DMARC compares the *visible* From domain against the *authenticated* domain: for SPF that is the **MAIL FROM / Return-Path** domain, for DKIM the signature's **`d=`** domain.

RFC 9989: "DMARC relies solely on SPF validation of the MAIL FROM identity" — **no fallback to the HELO name.** Default is *relaxed* for both (`adkim=r`, `aspf=r`), so `mail.yourdomain.com` aligns with `yourdomain.com` but `esp-bounces.com` does not.

**Why this bites:** many ESPs set their own bounce domain by default. SPF then passes — against *their* domain — and DMARC still fails. **DMARC passes if SPF *or* DKIM aligns; one is enough.** Fix with a custom bounce domain on your own domain (usually a CNAME the ESP provides), or with aligned DKIM.

---

## 3. Setting up a new platform — universal checklist

1. **Collect three things** from the platform's domain-authentication screen: its SPF `include:` value, its DKIM record (selector + TXT value, or CNAME target), and whether it offers a custom bounce/Return-Path domain.
2. **Read your current SPF record and write it down:** `nslookup -type=TXT yourdomain.com`.
3. **MERGE the new include into that record — never add a second SPF record.** Insert `include:newesp.com` before the `~all`, keeping every existing include.
4. **Count DNS lookups before publishing** (§4). If the ESP's template says `a mx` and you don't need them, drop them.
5. **Publish the DKIM record** exactly as given. Do not type your domain into the host field if the panel appends it automatically — that produces `sel._domainkey.you.com.you.com`.
6. **Publish DMARC** at `p=none` with a `rua=` address if not already there.
7. **Verify at the authoritative nameserver, not a cached one** — your ISP's resolver may serve a stale copy for the full TTL. Cross-check `8.8.8.8` for what the world sees.
   ```
   nslookup -type=NS yourdomain.com
   nslookup -type=TXT yourdomain.com ns1.dns-parking.com
   nslookup -type=CNAME sel._domainkey.yourdomain.com ns1.dns-parking.com
   ```
8. **Click the platform's Verify button** — most will not sign until they confirm the DNS themselves.
9. **Turn DKIM signing ON inside the platform.** A separate switch from publishing the record on nearly every platform, and the most common false-finish.
10. **Confirm the MAIL FROM / Return-Path domain** in settings, or off a test message's `Return-Path:` header. If it is the ESP's domain, set a custom bounce domain if offered — otherwise you rely entirely on DKIM alignment.
11. **Check List-Unsubscribe headers** on a real send (§7): both headers present, and an `https://` URI, not `mailto:` alone.
12. **Send a mail-tester probe** and fix what it flags (§5a).
13. **Send to a real Gmail address and read the raw headers** — `spf=pass`, `dkim=pass`, `dmarc=pass` (§5b). This is the gate; mail-tester is the rehearsal.
14. **Warm up** before any volume (§6).

---

## 4. The 10-lookup limit

RFC 7208 §4.6.4 caps SPF evaluation at **10 DNS-querying mechanisms**. Exceed it and you get `permerror` — SPF is treated as broken and **DMARC's SPF leg fails entirely.** A cliff, not a slope.

| Counts toward the 10 | Does NOT count |
|---|---|
| `include`, `a`, `mx`, `ptr`, `exists`, `redirect` | `all`, `ip4`, `ip6`, `exp` |

Same section: `mx` and `ptr` must each not query more than 10 address records, and implementations "SHOULD limit 'void lookups' to two" (queries returning nothing or NXDOMAIN). A dead include left behind after a switch burns void lookups.

**How to count:** each `include:` costs 1 *plus* whatever that include's own record costs, recursively. Ours costs **8** — `_spf.mail.hostinger.com` (1) → `relay.mail.hostinger.com` (2), `relay.mailchannels.net` (3); `jangomail.com` (4) → `spf-a`/`b`/`c`/`d` (5–8). Adding `a mx`, which JangoMail's template suggests, takes it to exactly 10 with zero headroom. **We did not add them.**

**At the ceiling:** (1) remove includes for platforms you no longer use — biggest win, and why §8 step 10 exists; (2) drop `a`/`mx` unless the domain's own server genuinely sends; (3) **[practice]** replace an include with its published `ip4:` ranges — 0 lookups, but you own the maintenance and break silently when the vendor renumbers; (4) **[practice]** an SPF flattening service, same trade.

---

## 5. Testing: three levels

### (a) mail-tester.com — the rehearsal
**Measures:** SPF/DKIM/DMARC results, SpamAssassin rule hits with point values, blacklist listings, message structure, broken links. **Does NOT measure:** whether Gmail puts you in Primary, Promotions, or Spam — Gmail does not use SpamAssassin. It publishes no scoring formula (research file, Open Question 6). A smoke alarm, not a grade. **A 10/10 message still lands in spam if your reputation is poor.**

### (b) Raw header inspection — the actual gate
Gmail → open message → ⋮ → **Show original**. Find `Authentication-Results:` (format per RFC 8601). A fully passing message shows all three:

```
Authentication-Results: mx.google.com;
       dkim=pass header.i=@scaleverticalwithai.com header.s=jm header.b=AbCdEf12;
       spf=pass (google.com: domain of bounce@scaleverticalwithai.com designates
         63.143.55.226 as permitted sender) smtp.mailfrom=bounce@scaleverticalwithai.com;
       dmarc=pass (p=NONE sp=NONE dis=NONE) header.from=scaleverticalwithai.com
```

| Line | What to check |
|---|---|
| `dkim=pass` | `header.i=`/`d=` must be **your** domain, not the ESP's — otherwise it passes but does not align |
| `spf=pass` | `smtp.mailfrom=` is the MAIL FROM domain. ESP's domain here = passes, does not align |
| `dmarc=pass` | `header.from=` is your visible domain. Passing means at least one of the two above aligned |
| `Return-Path:` | Separate header; same domain as `smtp.mailfrom` |
| `List-Unsubscribe:` + `-Post:` | Both required for one-click |

`dkim=none` means the platform is not signing — the switch, not the DNS.

### (c) Seed-inbox placement testing — the only real answer
6–10 mailboxes you control across Gmail, Outlook/Hotmail, Yahoo, and a custom domain. Include the panel in every send; a human records **Inbox / Promotions / Spam / Missing** for each. That grid is the only thing that tells you placement. Method already in `DELIVERABILITY-TEST-PLAN.md`; manual is sufficient, GlockApps/Inboxally can automate later. **[practice]** — no standard defines this. Also register the domain in **Google Postmaster Tools**, the only place you see your real Gmail complaint rate.

---

## 6. Warming a cold domain

**Why:** providers score domains on sending history. A new domain has none, so a burst of thousands reads exactly like a compromised account. Warming builds a record of small, well-received sends first.

**No provider publishes a ramp schedule. This whole table is [practice]**, built to stay under the documented thresholds in §7.

| Week | Daily volume | Audience |
|---|---|---|
| 1 | 20–50 | Seed panel + most engaged contacts only |
| 2 | 50–200 | Engaged only |
| 3 | 200–500 | Engaged, begin adding recent opt-ins |
| 4 | 500–1,500 | Widen gradually |
| 5+ | roughly double weekly while metrics hold | Full engaged segment |

**Watch every send:** bounce rate, complaint rate (Postmaster Tools), open rate, seed placement.

**Slow down or stop** when complaints exceed **0.3%** (Google's documented never-exceed), bounces exceed **2%** (**[practice]** — our circuit breaker from `DELIVERABILITY-TEST-PLAN.md`), seed placement shifts toward Spam, or opens fall sharply. Hold volume flat until it recovers; do not push through.

**Regulated niches ramp slower. [practice]** Men's health, supplements, finance, crypto, gambling attract heavier filtering and higher complaint rates than neutral B2B. Halve the table and hold each step two weeks. A risk judgement, not a documented rule.

**Warming does not rescue a cold list** — it blows past 0.3% complaints however clean your DNS is.

---

## 7. Gmail and Yahoo bulk sender requirements

Mandatory since 1 February 2024. Google defines bulk as **more than 5,000 messages/day to Gmail accounts**; Yahoo publishes no threshold. Both pages verified live 2026-07-24; no 2025/2026 changes announced.

| Requirement | Google | Yahoo |
|---|---|---|
| SPF **and** DKIM | Bulk (SPF *or* DKIM for all senders) | "Implement both SPF & DKIM" |
| DMARC published | Bulk; "can be set to none" | "at least p=none - DMARC must pass" |
| **Alignment** | From: "must be aligned with either the SPF domain or the DKIM domain" | Same wording |
| One-click unsubscribe | "must support one-click unsubscribe" + `List-Unsubscribe-Post: List-Unsubscribe=One-Click` | "supports one-click unsubscribe"; Post method "highly recommended" |
| Visible unsubscribe link in body | Required | Required |
| Honour unsubscribes | — | "within 2 days" |
| Spam complaint rate | "below 0.3%"; under 0.10% to be safe | "below 0.3%" |
| Forward + reverse DNS (PTR) | Required, all senders | Required |
| TLS on transmission | Required, all senders | — |
| RFC 5322 message format | Required, all senders | — |

**RFC 8058 one-click, exactly** (verified against the RFC): `List-Unsubscribe` "MUST contain one HTTPS URI" and may also carry a `mailto:`; `List-Unsubscribe-Post` "MUST contain the single key/value pair 'List-Unsubscribe=One-Click'." The receiver does an HTTPS **POST** to that URI with the pair as the body. A `mailto:`-only header is RFC 2369 and does **not** satisfy the requirement.

```
List-Unsubscribe: <https://example.com/unsubscribe/opaquepart>
List-Unsubscribe-Post: List-Unsubscribe=One-Click
```

**Ask every prospective platform in writing before committing:** *"Do you emit `List-Unsubscribe-Post: List-Unsubscribe=One-Click` per RFC 8058, and how is it enabled?"* A platform that cannot answer yes is disqualified for bulk sending to Gmail or Yahoo.

**RESOLVED for JangoMail (verified 2026-07-24 from live message headers):** JangoMail emits **both** headers automatically, no configuration needed:
```
List-Unsubscribe: https://track.scaleverticalwithai.com/u.z?j=..., mailto:UsingAIToScale@jangomail.com?Subject=Unsubscribe
List-Unsubscribe-Post: List-Unsubscribe=One-Click
```
**The transferable lesson: verify this from raw headers, never from vendor documentation.** JangoMail's public docs describe RFC 2369 only and made this look like a blocker; the actual sent message was compliant. Docs lag reality in both directions — send one test and read the headers.

---

## 8. Switching platforms

**Authenticate the new platform *before* removing the old.** Overlap is safe; a gap is not. Reputation lives on your **domain** and largely follows you — the new platform's **IP** reputation does not, which is why step 9 exists.

| # | Step |
|---|---|
| 1 | **Record the current state** — exact SPF value, DMARC value, DKIM host+value, raw headers of one recent good send. Your rollback. |
| 2 | **Add the new platform's SPF include,** merged into the one record. Both platforms coexist. |
| 3 | **Count lookups.** With both includes you are at peak count. If that exceeds 10, do steps 2 and 10 in the *same* change window and accept a brief gap. |
| 4 | **Publish the new DKIM record.** A different selector means no conflict; both live at once. |
| 5 | **Leave DMARC alone** — platform-independent. Never change policy mid-migration. |
| 6 | **Verify at the authoritative nameservers** (§3 step 7). |
| 7 | **Enable signing in the new platform, verify the domain there,** confirm the MAIL FROM domain, set a custom bounce domain if offered. |
| 8 | **Seed-panel send from the new platform.** Confirm `spf=pass`/`dkim=pass`/`dmarc=pass` and check placement. **Do not migrate the list until this passes.** |
| 9 | **Move production sending, then re-warm on the new IPs.** Domain reputation carries; the IPs do not. Ramp per §6 — faster than a cold start **[practice]**, but not zero-to-full in one send. |
| 10 | **After 2–4 weeks clean, remove the old platform's SPF include.** Frees lookups, closes an unneeded authorisation. **[practice]** on the interval — you wait for straggling automated sends. |
| 11 | **Remove the old DKIM record last, or leave it.** Orphaned DKIM is harmless and lets already-sent mail keep verifying. |

**Remove on switch:** the old ESP's SPF include; any custom bounce/Return-Path CNAME pointing at it; any old tracking-link CNAME.
**Leave alone:** DMARC; your host's business-mail SPF include (`_spf.mail.hostinger.com` — the domain still sends normal mail); MX records; the old DKIM selector unless it is in the way.

**Self-hosted platforms (e.g. Listmonk) add three items:** you supply the SMTP relay or IP, **you** own the PTR record, and **you** must emit `List-Unsubscribe-Post` yourself.

---

## 9. Troubleshooting

| Symptom | Likely cause | Fix |
|---|---|---|
| `spf=softfail` / `SPF_SOFTFAIL` | Sending IP not covered by any mechanism; `~all` caught it | Add the ESP's `include:`, merged into the one record. Never hard-code `ip4:<one IP>` — ESPs use many pools and it breaks on the next send |
| `spf=permerror` | Two `v=spf1` records, or more than 10 lookups | Delete the extra so exactly one remains; or cut includes/`a`/`mx` (§4) |
| SPF published, still failing | Cached resolver checked before propagation, or published on `www` not the root | Query the authoritative nameservers (§3 step 7); confirm host is `@` |
| DKIM published, `dkim=none` | Signing not switched on in the platform, or it never verified the DNS. (CNAME not resolving at all = the panel auto-appended your domain) | Toggle signing on, click Verify, re-test |
| `dkim=pass` but `dmarc=fail` | Signature `d=` is the ESP's domain — passing, not aligned | Sign with your domain, or fix SPF alignment via a custom bounce domain |
| `spf=pass` but `dmarc=fail` | Return-Path is the ESP's bounce domain (RFC 9989: MAIL FROM only, no HELO fallback) | Custom bounce domain on your domain, or rely on aligned DKIM |
| **Spam with all auth passing** | Reputation or engagement — tier 2, not tier 1 | Check Postmaster Tools complaint rate, cut volume, send only to engaged, re-warm. **Do not touch DNS** |
| Promotions tab, all auth passing | Categorisation, not filtering; Gmail documents no category signals | **[practice]** Fewer images, fewer tracked links, plainer HTML. Promotions is not spam |
| **Low mail-tester score, clean DNS** | Structure: invisible text, HTML-only, image-heavy with little text, URL shorteners, blacklisting | Read the *rule names*, not the number. `FONT_INVIS_*` = near-zero font size or `color:transparent`. `MIME_HTML_ONLY` = add a plain-text part **generated from** the HTML (writing a different one fires `MPART_ALT_DIFF`) |
| High bounces on a new platform | Suppression list never imported | Import old bounces and complaints **before** the first send |

---

## 10. Worked example: our JangoMail setup

`scaleverticalwithai.com` · DNS at Hostinger (`ns1/ns2.dns-parking.com`) · IP `63.143.55.226`, HELO `lsn025-i.jsmtp.net` · baseline mail-tester **3.6/10**.

| Record | Value | Note |
|---|---|---|
| SPF (TXT, `@`) | `v=spf1 include:_spf.mail.hostinger.com include:jangomail.com ~all` | Both includes needed — the domain also sends business mail via Hostinger. 8 of 10 lookups |
| DKIM (CNAME, `jm._domainkey`) | `jm._domainkey.jmsend.com` | JangoMail's docs describe a **TXT** record; the **CNAME** is what works. Headers beat documentation |
| DMARC (TXT, `_dmarc`) | `v=DMARC1; p=none` → add `rua=mailto:dmarc@scaleverticalwithai.com` | No reporting address = no visibility |

**Failure 1 — SPF.** The record authorised Hostinger only; `63.143.55.226` is nowhere in the Hostinger/MailChannels tree, so every receiver returned softfail. **Diagnosed by** resolving each include by hand and finding `ip4:63.143.55.128/25` inside `spf-c.jangomail.com`. **Trap avoided:** adding the `a mx` from JangoMail's own template takes the merged record from 8 to exactly 10 lookups — one upstream change from `permerror`.

**Failure 2 — invisible text.** A hidden preheader div carried `font-size:1px;line-height:1px;`, firing `__FONT_INVIS` for **2.499 points**. **The distinction that cost a wasted fix cycle:** the theory was "font colour matches background." That is a *different* rule — `HTML_FONT_LOW_CONTRAST` — worth **0.001**, i.e. nothing. `__FONT_INVIS` fires on exactly two things: a near-zero `font-size`/`font` value, or `color:transparent`. `display:none`, `opacity:0`, `visibility:hidden`, `max-height:0` do **not** trigger it. **Diagnosed by** reading the rule regex in Apache's source and walking the div through it.

**Safe preheader** — keep to exactly one hidden element per email:
```html
<div style="display:none;max-height:0px;overflow:hidden;mso-hide:all;">Preview text here.</div>
```

Both failures were invisible in the rendered email; both were found by reading primary sources — the DNS itself and the filter's rule file — not summaries.

---

## 11. Sources

**Standards**, fetched and verified 2026-07-24 — [RFC 7208 SPF](https://www.rfc-editor.org/rfc/rfc7208.html): §3.2 single-record rule, §4.6.4 lookup limits, `permerror` · [RFC 9989 DMARCbis](https://www.rfc-editor.org/rfc/rfc9989.html): alignment, relaxed default, SPF alignment on MAIL FROM only, `pct` removed, `t=` · [RFC 8058](https://www.rfc-editor.org/rfc/rfc8058.html): one-click headers, POST mechanics · RFC 8601: `Authentication-Results` format.

**Mailbox providers**, fetched and verified 2026-07-24 — [Google sender guidelines](https://support.google.com/a/answer/81126) · [Yahoo best practices](https://senders.yahooinc.com/best-practices/) · [Google DMARC rollout](https://knowledge.workspace.google.com/admin/security/set-up-dmarc)

**SpamAssassin rules**, carried from the research file — [`jhardin/20_misc_testing.cf`](https://svn.apache.org/repos/asf/spamassassin/trunk/rulesrc/sandbox/jhardin/20_misc_testing.cf) · [`20_html_tests.cf`](https://svn.apache.org/repos/asf/spamassassin/trunk/rules/20_html_tests.cf) · [`25_spf.cf`](https://svn.apache.org/repos/asf/spamassassin/trunk/rules/25_spf.cf) · [`20_body_tests.cf`](https://svn.apache.org/repos/asf/spamassassin/trunk/rules/20_body_tests.cf) · [`50_scores.cf`](https://svn.apache.org/repos/asf/spamassassin/trunk/rules/50_scores.cf)

**DMARC guidance** — [dmarc.org overview](https://dmarc.org/overview/) · [changes in DMARCbis](https://dmarc.org/2025/12/summary-of-changes-in-dmarcbis/)

**Vendor**, worked example only — [JangoMail SPF](https://jangomail.com/spf-records/) · [List-Unsubscribe](https://jangomail.com/email-deliverability-101-list-unsubscribe-header/) · [plain text](https://jangomail.com/plain-text-emails/) · [Litmus preview text](https://www.litmus.com/blog/the-ultimate-guide-to-preview-text-support). `support.jangomail.com` articles returned **HTTP 403** and could not be read.

**Project files** — `DELIVERABILITY-FIX-PLAN.md` · `DELIVERABILITY-TEST-PLAN.md`

**Tagged [practice], not documented requirement:** the engagement tier (§1); the whole warm-up ramp table and the slower ramp for regulated niches — no provider publishes a schedule; the 2% bounce circuit breaker (our governance, not a provider rule); the seed-panel method; SPF flattening and `ip4:` substitution; the 2–4 week wait before removing an old SPF include; the faster re-warm after a switch; the Promotions-tab advice.
