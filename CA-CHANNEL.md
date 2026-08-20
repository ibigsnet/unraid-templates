# CA channel

**Model (2026-08-20):**

| Branch | Role |
|--------|------|
| **`main`** | **CA / production** — catalog `PluginURL` and release tip |
| **`testing`** | Lab / WIP — frequent pushes; NIROG installs from here |
| ~~`stable`~~ | **Removed** — CA was slow to leave `main`; we flipped the model |

All `plugins/*.xml` **PluginURL** values must use each project’s **`main`** branch raw `.plg`.

| Wrong | Right |
|-------|--------|
| `…/ThunderboltNet/stable/…` | `…/ThunderboltNet/main/…` |
| `…/ThunderboltNet/testing/…` (in CA XML) | Lab-only; never put testing in the CA catalog |

CA AppFeed scrapes this repo. If Details → Repository still shows an old branch, bump `ExtraSearchTerms` (feed-nudge), push, wait for Squid’s scraper, then CA **Force Update**.

Installed flash `.plg` `pluginURL` is separate: Unraid **Update** follows flash, not the catalog.
- CA / production boxes: install from **main**
- Lab NIROG: install from **testing** raw URL so Update stays on the WIP loop

Promote workflow: soak on **testing** → merge **testing → main** and pin `.plg` entities to **main** (see `plugin-ops/promote-*-to-main.sh`).
