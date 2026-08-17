# unraid-templates

Community Applications catalog for **RifleJock / ibigsnet** Unraid plugins.

Install from the **Apps** tab on Unraid (search author **RifleJock**, or each plugin name below). Source and support links are on each app’s CA card and in the plugin repos.

| App | Description | Source | Install channel |
|-----|-------------|--------|-----------------|
| **Storage Guard** | Free-space thresholds and Main free-bar coloring | [StorageGuard](https://github.com/ibigsnet/StorageGuard) | `main` |
| **Thunderbolt Net** | Host-to-host networking over Thunderbolt / USB4 | [ThunderboltNet](https://github.com/ibigsnet/ThunderboltNet) | `main` |
| **Fabric Routing** | Optional FRR packages (OpenFabric and friends) | [FabricRouting](https://github.com/ibigsnet/FabricRouting) | `main` |
| **NBD Export** | Network block device export and imaging | [NBDExport](https://github.com/ibigsnet/NBDExport) | `main` |

Docker templates may be added under `templates/` later.

## How CA finds these apps

1. This catalog repo is **`main` only** (`github.com/ibigsnet/unraid-templates`).
2. Each `plugins/*.xml` **`PluginURL`** points at that plugin’s **`main`** branch raw `.plg` on GitHub (lab + production for now).
3. Community Applications re-scrapes the feed periodically (see Apps → CA settings / last feed change). After a catalog push, expect a delay before every host sees it.

### Manual install (same as CA)

| Plugin | Raw `.plg` |
|--------|------------|
| Storage Guard | `https://raw.githubusercontent.com/ibigsnet/StorageGuard/main/storageguard.plg` |
| Thunderbolt Net | `https://raw.githubusercontent.com/ibigsnet/ThunderboltNet/main/thunderboltnet.plg` |
| Fabric Routing | `https://raw.githubusercontent.com/ibigsnet/FabricRouting/main/fabricrouting.plg` |
| NBD Export | `https://raw.githubusercontent.com/ibigsnet/NBDExport/main/nbd.plg` |

**Legacy names:** do not use `NbdExport`, `UnraidFRR`, or old `install.plg` paths — CA and plugins use the names above.

## Support

- Unraid forum threads linked from each plugin (where available)
- GitHub Issues on each source repository
- Development: [Patreon](https://www.patreon.com/cw/IBIGSNet) · [PayPal](https://www.paypal.com/paypalme/RifleJock)

## License

GNU GPLv3 or later — **ibigs, LLC** (Author: RifleJock). See [LICENSE](LICENSE).

---

This repository was previously named `unraid-docker-templates`. GitHub keeps that URL working via redirect.
