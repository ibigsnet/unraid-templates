# CA channel

All `plugins/*.xml` **PluginURL** values must use each project’s **`stable`** branch raw `.plg`.

| Wrong | Right |
|-------|--------|
| `…/ThunderboltNet/main/thunderboltnet.plg` | `…/ThunderboltNet/stable/thunderboltnet.plg` |
| `…/StorageGuard/main/…` | `…/StorageGuard/stable/…` |

CA AppFeed scrapes this repo. **Details → Repository** is the feed’s copy of `PluginURL`. If it still shows `/main/` while this tree says `/stable/`, the feed is stale — bump `ExtraSearchTerms` (or any template field), push, wait for Squid’s scraper, then CA **Force Update**.

Installed flash `.plg` `pluginURL` is separate: Unraid **Update** follows flash, not the catalog. Lab (NIROG) may stay on `/main/`; CA/production boxes should reinstall from the stable URL if flash is locked to main.

Production freeze lifted 2026-08-19: Thunderbolt Net stable tip **2026.08.18ar** (explicit promote).
