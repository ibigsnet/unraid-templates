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
| [Thunderbolt Net](plugins/thunderboltnet.xml) | Plugin | Thunderbolt 3/4/5 + USB4/v2 host-net — [ibigsnet/ThunderboltNet](https://github.com/ibigsnet/ThunderboltNet) |
| [Fabric Routing (FRR)](plugins/fabricrouting.xml) | Plugin | Optional FRR packages/daemons — [ibigsnet/FabricRouting](https://github.com/ibigsnet/FabricRouting); pairs with Thunderbolt Net for OpenFabric |
| [NBD Export](plugins/nbdexport.xml) | Plugin | Block export/imaging — [ibigsnet/NbdExport](https://github.com/ibigsnet/NbdExport); Network Services → NBD |

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
| `LICENSE` | GPLv3 |

## Layout notes

- One XML file per Docker app under `templates/`
- One XML wrapper per plugin under `plugins/`


## Why an app is missing from Community Applications

Layout here matches the [CA starter](https://github.com/unraid/unraid-community-apps-starter): `ca_profile.xml`, `plugins/*.xml`, optional `templates/`.

Common reasons a plugin does not appear even though the XML is on GitHub:

1. **PluginURL must match the `.plg` `pluginURL` entity exactly** (no extra `?v=`). CA documents this as required.
2. **Invalid or exotic IconFA** — prefer Font Awesome **4.7** names (`shield`, `sitemap`, `database`).
3. **Appfeed scan lag / rejection** — on Unraid open **Apps → Statistics** and check **Template Errors** / **Invalid Templates** and last feed time (~2 hours typical).
4. **New plugins** can need a **Validate + Scan** pass at [ca.unraid.net/submit](https://ca.unraid.net/submit) (plugin entries are reviewed).
5. Search by **Name** or **ExtraSearchTerms** (e.g. FRR, NBD), not only old Overview wording.

Working pair for reference: Storage Guard and Thunderbolt Net (same `plugins/` layout).

6. **Wrong branch** — production PluginURL must be `stable` (exact match to `.plg` entity), not a half-finished `main` tree.


## License

GNU GPLv3 or later — copyright **ibigs, LLC** (Author: RifleJock). See [LICENSE](LICENSE).

## Release channel (`stable`)

CA PluginURLs point at each plugin's GitHub **`stable`** branch, not `main`.

| Plugin | PluginURL |
|--------|-----------|
| Storage Guard | `…/StorageGuard/stable/storageguard.plg` |
| Thunderbolt Net | `…/ThunderboltNet/stable/thunderboltnet.plg` |
| Fabric Routing | `…/FabricRouting/stable/fabricrouting.plg` |
| NBD Export | `…/NbdExport/stable/install.plg` |

Policy: [RELEASE-CHANNEL.md](RELEASE-CHANNEL.md). Develop on `main` in each plugin repo; ship by merging to `stable`.

Security / review notes live in each plugin's `SECURITY.md`.
