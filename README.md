# GeoWatch Dashboard

Public static frontend for the private GeoWatch / NASA FIRMS monitoring backend.

## Purpose

This repository exists only because GitHub Pages on the current plan cannot be served from the private backend repository.

Backend source, database migrations, recovery documentation and operational logic remain private in:
`koi2mkXSZ/NASA-FIRMS`.

## Security model

This repository must contain **no secrets**.

Allowed:
- static HTML/CSS/JavaScript;
- GitHub Pages workflow;
- public documentation.

Never commit:
- Supabase `service_role`;
- cron/HMAC secret;
- Telegram bot token or chat IDs;
- database credentials;
- Vault values;
- private reports or database dumps.

The dashboard is opened from the private Telegram admin panel. The bot creates a short-lived signed URL. The browser sends only `exp` and `sig` to the Supabase Edge API; authorization and service-role database access occur server-side.

## Production

- Pages: `https://koi2mkxsz.github.io/GeoWatch-Dashboard/`
- API: Supabase Edge Function `firewatch-dashboard`
- Mode: read-only
- Signed-link TTL: 4 hours
- Hard accepted maximum: 12 hours
- Refresh: 60 seconds

## Deployment

GitHub Pages source: **GitHub Actions**.

Workflow:
`.github/workflows/pages.yml`

Every change to `index.html` deploys automatically.

## Canonical recovery documentation

The private backend repository is the source of truth for:
- `RECOVERY.md`
- `SYSTEM_MANIFEST.md`
- `BACKUP_POLICY.md`
- `OPERATIONS.md`
