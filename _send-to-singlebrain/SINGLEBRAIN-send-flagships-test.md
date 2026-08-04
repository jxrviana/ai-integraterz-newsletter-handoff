# → SingleBrain: load + TEST-send The Referral Channel + The Dealmaker Issue 1

*(Xander: paste this + attach both zips. It loads both into ListMonk and sends a TEST to xander@ + justin@ ONLY. The real send HOLDS for Xander's explicit go.)*

Load these two as ListMonk campaigns. Zips attached (each = `index.html` + `images/`):
- `the-referral-channel.zip`
- `the-dealmaker-issue-1.zip`

## Per-newsletter setup
| | The Referral Channel | The Dealmaker (Issue 1) |
|---|---|---|
| **SMTP** | **Bird** | **Resend** |
| **From** | The Referral Channel `<referral@send.usingaitoscale.com>` | The Dealmaker `<dealmaker@send.usingaitoscale.com>` |
| **Reply-To** | `xander@usingaitoscale.com` | `xander@usingaitoscale.com` |

*(Different SMTP per newsletter is intentional — if one gets flagged, the other is protected.)*

## For BOTH — same mechanics that worked for Dealmaker 2
- **BLANK / raw ListMonk template** (whole body = `{{ template "content" . }}`, no wrapper, no border, no ListMonk footer) — our HTML is already a complete email.
- **Host the images via the media API**; point each `<img src>` at the hosted URLs.
- **Merge tags:** `{{VIEW_ONLINE_LINK}}` → `{{ MessageURL }}`, `{{UNSUBSCRIBE_LINK}}` → `{{ UnsubscribeURL }}`.
- **Reply-To must be set** to `xander@usingaitoscale.com` (the From domain is send-only — without Reply-To, replies bounce).

## Then — TEST SEND ONLY
- Send a test of EACH campaign to **`xander@usingaitoscale.com` + `justin@usingaitoscale.com` only.**
- **Do NOT send to any list.** After the test, Xander reviews it in his inbox + the ListMonk preview and gives the explicit **GO** before the real send.

## Intended real send — HOLD until Xander says go
- The Referral Channel → the master list via **Bird**.
- The Dealmaker Issue 1 → the master list via **Resend**.
- List = `ALL-LEADS-unified.csv` (~19k, already includes the xander@/justin@ seeds) — Xander provides it.
- ⚠️ **Final volume is still being decided — do NOT send to the full list until Xander confirms the number and gives the explicit go.**

Report when both tests are delivered and the previews render correctly (images showing, no box, links + unsubscribe working).
