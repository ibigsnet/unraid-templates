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

## Existing installs that still point at `main`

Older Storage Guard / Thunderbolt Net installs used PluginURL on `main`. Version **2026.08.14aa** on `main` migrates them: after that update, the installed `.plg` has PluginURL=`stable` and future updates come only from `stable`.

## Development discipline (avoid shipping WIP)

On `main`, keep `pluginURL` and `raw` pointed at **`stable`** (already set). That way even a stale bookmark to a `main` `.plg` URL still installs **stable** files.

When developing:

1. Change code on `main` freely.
2. **Do not bump** the `.plg` version entity until you are ready to ship.
3. To lab-test unreleased code, temporarily point `raw` at `main` on a private build, or copy files by hand — do not push a higher version on `main` than on `stable` unless you are shipping.
4. Ship: bump version → commit → merge/push `main` → fast-forward `stable` to the same commit → push `stable`.

Never leave `stable` behind a higher version number that only exists on `main`.
