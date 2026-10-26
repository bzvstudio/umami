# Umami (Self-Hosted)

This repository is a fork of the official Umami analytics project,
configured for **controlled self-hosting**.

Production deployments are pinned to a specific release version.
Updates are **manual by design**.

---

## Branches

- `master`  
  Tracks the upstream Umami repository.  
  **Do not deploy from this branch.**

- `main`  
  Production branch.  
  Deployed to Railway and pinned to a specific Umami release.

---

## Updating Umami

Updates are performed manually to ensure stability.

### 1. Fetch upstream changes and tags

```bash
git fetch upstream --tags
```

### 2. Back up the database first

Migrations run automatically on container start and cannot be rolled back.
Railway Postgres is Postgres 17, so use a matching `pg_dump`:

```bash
docker run --rm -e DB="$DATABASE_PUBLIC_URL" -v ~/umami-backups:/out postgres:17 \
  sh -c 'pg_dump -Fc --no-owner "$DB" -f /out/umami-prod-$(date +%F).dump'
```

### 3. Merge the release tag into `main` and push

```bash
git checkout main
git merge vX.Y.Z
git push origin main
```

---

## Release history

- **2026-10-26**: v3.0.3 → v3.4.1. Fixed the Railway build failure (unpinned pnpm in the
  old Dockerfile). Applied migrations 15–26; row counts verified identical before/after.
