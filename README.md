# unraid-templates

Community Applications repository for **RifleJock / ibigsnet**.

## Repository move

This repo was renamed / moved from:

**https://github.com/ibigsnet/unraid-docker-templates**

→ **https://github.com/ibigsnet/unraid-templates**

GitHub redirects the old URL. Use **unraid-templates** for CA submit and new links.

## Contents

| App | Type | Notes |
|-----|------|--------|
| [Storage Guard](plugins/storageguard.xml) | Plugin | Source: [ibigsnet/StorageGuard](https://github.com/ibigsnet/StorageGuard) |

Docker templates (e.g. Neos / Resonite headless) will be re-added under `templates/` later.

## CA submit URL

```
https://github.com/ibigsnet/unraid-templates
```

Portal: https://ca.unraid.net/submit

## Layout

| Path | Purpose |
|------|---------|
| `ca_profile.xml` | CA repository profile / icon / donate |
| `plugins/` | Plugin wrappers (`PluginURL` → raw `.plg`) |
| `templates/` | Docker application templates (empty for now; CA expects Docker XML here) |
| `icon.png` | Repository icon |
| `LICENSE` | MIT |

## Layout notes

- One XML file per Docker app under `templates/`
- One XML wrapper per plugin under `plugins/`
