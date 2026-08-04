---
name: listmonk
description: Operate a listmonk newsletter server via its REST API — manage lists, add/import subscribers, create and send campaigns, send transactional email, check stats. Use when asked to "send a newsletter", "add subscribers", "create a campaign", "email the list", "import contacts into listmonk", or anything involving listmonk.
---

# Listmonk Operations

Drive a self-hosted [listmonk](https://listmonk.app) instance (newsletter + mailing list manager, Mailchimp alternative) through its REST API.

## Setup (once per machine)

The skill reads connection details from environment variables (put them in your shell profile or the project's `.env.local`):

```bash
export LISTMONK_URL="https://listmonk-production-2930.up.railway.app"  # your instance, no trailing slash
export LISTMONK_USER="admin"          # admin username OR an API user name
export LISTMONK_TOKEN="..."           # that user's password OR API token
```

Prefer a dedicated API user over admin credentials: in the listmonk admin UI go to **Admin → Users → + New**, choose type **API**, copy the generated token, and use that as `LISTMONK_USER`/`LISTMONK_TOKEN`.

If these vars are unset, ask the user for their listmonk URL and credentials before doing anything else.

## The helper script

All operations go through [scripts/lm.sh](scripts/lm.sh) (curl wrapper, auto-auth, pretty-prints JSON):

```bash
scripts/lm.sh health                          # connectivity check — RUN THIS FIRST
scripts/lm.sh lists                           # list all mailing lists
scripts/lm.sh create-list "Weekly Digest" public single
scripts/lm.sh subs [list_id]                  # subscribers (optionally filter by list)
scripts/lm.sh add-sub jane@x.com "Jane Doe" 1,2   # email, name, list IDs (pre-confirmed)
scripts/lm.sh campaigns                       # list campaigns
scripts/lm.sh create-campaign "Name" "Subject line" 1,2 body.html   # lists + HTML body file
scripts/lm.sh test-campaign 3 me@x.com        # send test of campaign 3
scripts/lm.sh start-campaign 3                # START SENDING campaign 3 (confirm first!)
scripts/lm.sh tx 2 jane@x.com '{"order_id":"123"}'   # transactional send: template, recipient, data
scripts/lm.sh raw GET /api/settings           # any other endpoint
scripts/lm.sh raw POST /api/lists '{"name":"VIP","type":"private","optin":"single"}'
```

For anything the script doesn't cover, use `raw` with the endpoint reference in [references/api.md](references/api.md).

## Workflow rules

1. **Always `health` first** in a session — fail fast on bad URL/credentials.
2. **Campaign sending is irreversible.** Before `start-campaign`: show the user the campaign subject, body summary, and recipient count (`GET /api/campaigns/{id}` → `lists`, and subscriber counts), send them a `test-campaign` to their own address if they want one, and get explicit confirmation. Never start a campaign unprompted.
3. **Bulk imports**: for >100 subscribers use the CSV import endpoint (see references/api.md § Import) rather than looping `add-sub`.
4. **Subscribers added via API** with `preconfirm_subscriptions: true` skip double opt-in — only do this for contacts who already consented.
5. SMTP must be configured in the admin UI (Settings → SMTP) before anything sends. If sends fail, check that first, then `GET /api/logs`.
6. Content: campaigns accept `content_type` of `richtext`, `html`, `markdown`, or `plain`. Use `{{ .Subscriber.FirstName }}`-style Go template tags for personalization; `{{ UnsubscribeURL }}` is auto-appended by the default template.

## Common recipes

**"Send this newsletter to my list":** health → `lists` (find target list id + subscriber count) → write HTML body to a temp file → `create-campaign` → `test-campaign` to the user's own email → report recipient count and wait for user's go-ahead → `start-campaign` → poll `GET /api/campaigns/{id}` until `status: finished`, report sent count.

**"Add these people to the list":** health → `lists` → `add-sub` per contact (or CSV import for many) → confirm final count via `subs <list_id>`.

**"How did the last campaign do?":** `campaigns` → read `views`, `clicks`, `sent`, `bounces` from the response; `GET /api/campaigns/analytics/*` endpoints for detail.
