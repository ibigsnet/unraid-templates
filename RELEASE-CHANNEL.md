# Release channel

| Branch (plugin repos) | Role | PluginURL / `raw` |
|----------------------|------|-------------------|
| `main` | Development / lab | `…/main/…` |
| `stable` | CA / end users | `…/stable/…` |

This repo’s `plugins/*.xml` always use **stable** PluginURLs.

## Ship (production)

1. Test on lab from `main`.
2. Bump version; set `pluginURL` + `raw` (+ FRR catalog if needed) to **stable**.
3. Push `main`, fast-forward and push `stable`.
4. Confirm CA XML `PluginURL` matches the stable `.plg` entity.

Do not leave a higher version only on `main`.

## Lab

Prefer uninstall → install from `main` raw URLs when exercising cold install/remove.  
CA users stay on **Update** from `stable`.

## Version dates

Use the lab wall-clock date (America/Chicago) for `YYYY.MM.DD` versions.  
Same day → two-letter suffixes (`aa`, `ab`, …). Do not invent tomorrow.  
Full rules: each plugin `RELEASES.md`.
