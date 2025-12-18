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
