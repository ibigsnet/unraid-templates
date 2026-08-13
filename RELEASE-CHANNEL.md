# Release channel policy

## Branches

| Branch | Purpose |
|--------|---------|
| `main` (each plugin repo) | Active development. May be broken. Not what CA should install. |
| `stable` (each plugin repo) | Production channel for Community Applications and end users. |

## PluginURL rule

Every shipped `.plg` must set:

- `pluginURL` → `https://raw.githubusercontent.com/ibigsnet/<Repo>/stable/<file>.plg`
- `raw` → `https://raw.githubusercontent.com/ibigsnet/<Repo>/stable`

CA wrappers in `plugins/*.xml` must use the **same** PluginURL string (exact match).

## Ship checklist

1. Finish and test on `main` (lab install from main only if you temporarily need it).
2. Merge or cherry-pick the release commit(s) to `stable`.
3. Confirm version entity sorts after the previous ship (`YYYY.MM.DD` + two-letter suffix).
4. Push `stable` (and `main`).
5. Confirm raw URLs 200 and PluginURL entity matches CA XML.
6. After feed update, search CA for the app.

## License

Plugin templates and wrappers: **GPL-3.0-or-later**, copyright **ibigs, LLC** (Author: RifleJock).

GPLv3 is standard for Unraid plugins and is **not** a Community Applications blocker.
