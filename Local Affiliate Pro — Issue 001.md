# Local Affiliate Pro - Issue 001 verified-offer ledger

Research date: 2026-08-04. Updated after browser verification. Draft only. No sends or tests performed.

## Included offers

| # | Offer | Canonical URL | Browser verification and exact supporting line | Evidence permits |
|---:|---|---|---|---|
| 1 | Shopify Affiliate Program | https://www.shopify.com/affiliates | Browser page: “Get paid to refer new merchants to Shopify.” It also states: “Calculations are estimates only. Commissions are paid for every signup to the Basic, Grow or Advanced paid plans. Commission amounts vary by referral location.” | Product/program existence and stated commission mechanics; no fixed commission rate claimed. |
| 2 | HubSpot Affiliate Program | https://www.hubspot.com/partners/affiliates | Browser page: “Earn 30% recurring commission for every customer your refer successfully (up to $1,000+ per sale).” It further states: “30% monthly recurring commission for up to one year.” | 30% recurring commission, up to one year, as stated on the official page. |
| 3 | GetResponse Affiliate Program | https://www.getresponse.com/affiliate-programs | Browser page: “Earn up to 60% commission for every referral.” It also states: “Earn up to 60% per sale. For every paying customer who signs up with your link, you'll earn up to 60% recurring commission.” | Up to 60% commission claim, with the page's tier and recurring-commission caveats. |
| 4 | Speaker Agent | https://speakeragent.ai/ | Browser page: “We connect you directly to podcast hosts and show producers.” It also states: “Your free tier includes 1 Scout run and voice samples.” | Platform existence and described functionality. Public affiliate payout terms were not located; no payout claim is made. |
| 5 | FreshBooks Affiliate Program | https://www.freshbooks.com/affiliate-program | Browser page: “Monetize your referrals with trackable links, approved resources, and performance insights through PartnerStack, our affiliate program platform.” The page also labels the offer “FRESHBOOKS AFFILIATE PROGRAM.” | Affiliate-program existence and tracking/resource functionality. The public page did not expose a specific commission figure in the browser view, so none is claimed. |
| 6 | ActiveCampaign Affiliate Program | https://www.activecampaign.com/partners/affiliate | Browser page: “When you share ActiveCampaign through your affiliate link, you can earn a 30% recurring commission on the subscription price paid.” It also states: “You’ll get 30% of the subscription value for each paying customer you refer for up to 12 months.” | 30% recurring commission, up to 12 months, as stated on the official page. |
| 7 | The Affiliate Machine | https://theaffiliatemachine.com/ | Browser page title: “The Affiliate Machine.” The page describes “a 'done for you' digital marketing course” and a “MASTER RESELL RIGHTS OPPORTUNITY.” | Offer existence and description. Public affiliate payout terms were not located; no payout claim is made. |
| 8 | Kinsta Hosting Affiliate Program | https://kinsta.com/affiliates/ | Browser page: “Join our high-paying affiliate program and earn a one-time bonus of up to $500, plus lifetime monthly commissions of 10% for every referral to Kinsta’s Managed Hosting for WordPress.” | One-time bonus up to $500 and lifetime monthly commissions of 10%, as stated on the official page. |
| 9 | ConnectMed | https://myconnectmed.com/ | Browser page: “Our turnkey platform gives your members access to 50+ premium wellness products” and describes providers, compliance, and fulfillment. | Platform existence and described wellness-business functionality. Public affiliate payout terms were not located; no payout claim is made. |
| 10 | monday.com Affiliate Program | https://monday.com/affiliate-program | Browser page: “With our tier model, you can earn up to 100% commission on the first year’s sales of each customer you refer.” | Up to 100% commission on first-year sales, as stated on the official page. |
| 11 | Hostinger Affiliate Program | https://www.hostinger.com/affiliates | Browser page: “Join an affiliate program that values your partnership - it's completely free of charge!” The page lists “Track your performance,” “Use affiliate banners,” “Get your payout,” and “Commissions based on performance.” | Affiliate-program existence, free-to-join statement, tracking/assets/payout references, and performance-based commissions. No numeric rate is claimed because none was visible on the official page. |

## Required offer-bank gap

| Offer | Status | Reason omitted |
|---|---|---|
| Pinnacle Funding | **Omitted - unverified** | No canonical live public affiliate/program URL and terms were supplied or independently confirmed. It is not present in the customer-facing HTML. |

## QA notes

- Visible offer numbers are sequential 01 through 11.
- Third-party programs lead the issue; the three internal offers are interspersed at positions 04, 07, and 09.
- CSS is fully inline. There is no `<style>` block.
- Curly punctuation and the copyright symbol were converted to HTML entities or ASCII. The only typographic entity retained is `&copy;`; the CTA uses `&mdash;` and the issue separator uses `&middot;`.
- No social links, sign-up links, images, Medium article, or news-card structure.
- Required merge tags only: `{{ MessageURL }}` and `{{ UnsubscribeURL }}`.
- From: `Local Affiliate Pro <local-affiliate-pro@send.usingaitoscale.com>`
- Reply-To: `xander@usingaitoscale.com`
- No email, test, campaign update, or send performed.

<!-- Verification distinction: official pages establish only the claims shown above. Program approval, geography, payout timing, attribution window, and current terms must be checked before any future send. -->

## Browser verification URLs

All 11 included canonical URLs were opened in the browser during this update. The browser returned live program/product pages for each. Pinnacle Funding remains excluded pending a canonical URL and terms.

## Note on FreshBooks and Hostinger

The requested browser check was completed. FreshBooks' live page confirms the affiliate program, PartnerStack tracking/resources, and affiliate-partner structure but did not expose a numeric commission in the browser text. Hostinger's live page confirms the affiliate program, free-to-join statement, tracking, banners, payout section, and performance-based commissions but did not expose a numeric rate in the browser text. Accordingly, the HTML avoids unsupported numeric claims for both.

## Note on Shopify

Shopify's browser page confirms commissions are paid for signups to Basic, Grow, or Advanced paid plans and that commission amounts vary by referral location. It does not present a universal fixed rate in the visible page text, so the HTML makes no fixed-rate claim.

## Note on HTML attachment

The HTML file is preserved at `/opt/data/local-affiliate-pro/issue-001/index.html` for attachment. This remains a review draft and is not send-ready.

<!-- Research ledger generated for Local Affiliate Pro Issue 001. -->
<!-- The customer-facing copy intentionally omits unverified Pinnacle Funding. -->
<!-- No images are referenced, so no Higgsfield prompt handoff is required. -->
