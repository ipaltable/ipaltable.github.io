# paltable.com marketing site (source)

Static homepage + legal pages. **Deployed via the unified Vercel app** in `restaurant-portal/` — not as a separate project.

| Edit here | Live at |
|-----------|---------|
| `website/index.html` | `paltable.com/` |
| `website/privacy/` etc. | `/privacy` `/terms` `/eula` |
| `restaurant-portal/src/` | `/login` `/dashboard` … |

Deploy guide: [`scripts/VERCEL_SETUP.md`](../scripts/VERCEL_SETUP.md)

## Pages

| Path | File |
|------|------|
| `/` | `index.html` |
| `/privacy` | `privacy/index.html` (synced from `legal/privacy.html`) |
| `/terms` | `terms/index.html` |
| `/eula` | `eula/index.html` |
| `/restaurants` | `restaurants/index.html` |
| `/login` | `login/index.html` (mock restaurant portal sign-in) |
| `/restaurants/dashboard/*` | Static mock portal (dashboard, menu, events, …) |

## Workflow

1. Edit `website/` or `legal/`
2. Push to `main`
3. Vercel builds `restaurant-portal/` — `prebuild` runs `./scripts/sync-website-to-portal.sh`

Local preview of the **full** site (marketing + portal):

```bash
./scripts/setup-vercel-portal.sh
cd restaurant-portal && npm run dev
# http://localhost:3000/  http://localhost:3000/login
```

Sync marketing into portal public/ only:

```bash
./scripts/sync-website-to-portal.sh
```

## Sync legal content

```bash
./scripts/sync-legal-to-website.sh
```

## Assets

Homepage media: `website/assets/` (`favicon.png`, `logo_transparent.png`, `hero1.mp4`).

## GitHub Pages (optional backup)

`.github/workflows/github-pages-marketing.yml` — do not use for `paltable.com` if Vercel is primary.
