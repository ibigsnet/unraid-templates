# unraid-templates

Community Applications catalog for **RifleJock / ibigsnet** Unraid plugins.

Layout matches the [Community Apps starter](https://github.com/unraid/unraid-community-apps-starter): `ca_profile.xml`, `LICENSE`, `icon.svg`, `plugins/*.xml`. There are no Docker templates.

| App | CA install (`PluginURL`) | Source |
|-----|--------------------------|--------|
| **Storage Guard** | `…/StorageGuard/**main**/storageguard.plg` | [StorageGuard](https://github.com/ibigsnet/StorageGuard) |
| **Thunderbolt Net** | `…/ThunderboltNet/**main**/thunderboltnet.plg` | [ThunderboltNet](https://github.com/ibigsnet/ThunderboltNet) |
| **Fabric Routing** | `…/FabricRouting/**main**/fabricrouting.plg` | [FabricRouting](https://github.com/ibigsnet/FabricRouting) |
| **NBD Export** | `…/NBDExport/**main**/nbd.plg` | [NBDExport](https://github.com/ibigsnet/NBDExport) |

- This catalog repo: branch **`main` only** (CA reads XMLs here).
- Plugin wrappers: `plugins/*.xml` (`<Plugin>`). Root `*.xml` copies exist for the older AppFeed parser; both point at the same `/main/` `.plg`.
- Each plugin **install/update** URL: that project’s **`main`** branch. `PluginURL` here must match the `pluginURL` entity inside that `.plg`.
- Lab/WIP: install from each project’s **`testing`** raw `.plg`. CA installs **`main`**.

## Support

- Forum / GitHub links on each CA card
- [Patreon](https://www.patreon.com/cw/IBIGSNet) · [PayPal](https://www.paypal.com/paypalme/RifleJock)

## License

GNU GPLv3 or later — **ibigs, LLC** (Author: RifleJock).
