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

Squid’s registered URL in [Repositories.json](https://github.com/Squidly271/Community-Applications-Moderators/blob/master/Repositories.json) must be `https://github.com/ibigsnet/unraid-templates`. As of 2026-08-28 it still lists **`https://github.com/ibigsnet/unraid-docker-templates`**. That name 301s on GitHub, so CA Details can show the new repo name while the AppFeed clone path stays `/tmp/GitHub/repositoryClone/ibigsnet/unraid-docker-templates` on the pre-rename tree (old docker XML only). Fix is Squid updating that URL and deleting the old clone dir. A feed-nudge alone will not unstick that clone.

**XML shape for the live AppFeed:** working CA plugins (desertwitch, jcofer555, …) use root `<Containers>` + `<Plugin>True</Plugin>` + `<PluginURL>`, usually as `*.xml` at the **repo root**. The newer ca.unraid.net starter uses `<Plugin>` wrappers under `plugins/`. Production scrape still expects the Containers form. Catalog XMLs are kept in both places (same PluginURL; CA should dedupe).

Installed flash `.plg` `pluginURL` is separate: Unraid **Update** follows flash, not the catalog.
- CA / production boxes: install from **main**
- Lab NIROG: install from **testing** raw URL so Update stays on the WIP loop

Promote workflow: soak on **testing** → merge **testing → main** and pin `.plg` entities to **main** (see `plugin-ops/promote-*-to-main.sh`).
