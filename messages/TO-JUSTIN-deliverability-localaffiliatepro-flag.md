**Deliverability blocker on Local Affiliate Pro — and it's a domain-reputation fix that's yours, Justin.**

LAP is built and the content is done. But the test send lands in **spam**, and clicking the CTA throws Google's **"this link is dangerous"** warning. I diagnosed it end to end — here's the clean version.

**The good news — our sending setup is healthy.** mail-tester confirms:
- **SPF: pass.** **DKIM: valid and aligned** to `send.usingaitoscale.com`.
- **Sending IP reputation: excellent** — Bird IP `192.174.87.116` is on Mailspike's good-senders list.
- Auth and IP are **not** the problem. Those are done right.

**The problem is one thing: the `localaffiliatepro.com` link is burned.**
- **Google Safe Browsing has flagged `localaffiliatepro.com`** as harmful. Confirmed: the "See Who's Building" button links straight to `localaffiliatepro.com/agencies/`, and clicking it triggers Chrome/Gmail's danger screen. You can see it at `transparencyreport.google.com/safe-browsing/search`.
- **mail-tester confirms it independently:** the email is in the **Razor2 collaborative spam database at 100% confidence** — that's the entire negative score. The content/links are already fingerprinted as spam.
- Almost certainly flagged from the **Referral Channel Issue 1** blast, which used this same `localaffiliatepro.com/agencies/` link to ~18.5k.
- A flagged link in the body is why Gmail spam-folders it — Gmail runs every link through Safe Browsing.

**What I need from you (this is the domain/infra lane):**
1. **Clear the Safe Browsing flag** — in Google Search Console for `localaffiliatepro.com`: **Security Issues → Request Review.** Google re-scans and lifts it in a few days if the site's clean.
2. **Give us a clean CTA destination for the meantime** — we can't link to a flagged domain. Either a different/fresh URL for the button, or we hold LAP until `localaffiliatepro.com` clears. *(Also: `/agencies/` currently just redirects to the homepage — worth pointing the CTA somewhere that actually resolves.)*
3. **(Recommended) Move ListMonk onto a real custom domain** (e.g. `mail.usingaitoscale.com`) so links, images, and unsubscribe stop coming from the `railway.app` subdomain — that's a secondary spam signal we'll want gone before scaling.

**The upside:** because auth + IP are already clean, the moment we swap to a clean destination, deliverability should jump. The build is finished and good.

**My recommendation: hold the 18,847-send until #1 and #2 are resolved.** Sending it now means it all lands in spam and adds ~18.8k more spam reports against the domain — making the flag harder to reverse.
