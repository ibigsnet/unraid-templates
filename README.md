# unraid-templates

Community Applications repository for **RifleJock / ibigsnet**.

Former name: `unraid-docker-templates` (GitHub redirects). Submit this repo at [ca.unraid.net/submit](https://ca.unraid.net/submit):

```
https://github.com/ibigsnet/unraid-templates
```

## Apps

| App | Wrapper | Source |
|-----|---------|--------|
| Storage Guard | [plugins/storageguard.xml](plugins/storageguard.xml) | [StorageGuard](https://github.com/ibigsnet/StorageGuard) |
| Thunderbolt Net | [plugins/thunderboltnet.xml](plugins/thunderboltnet.xml) | [ThunderboltNet](https://github.com/ibigsnet/ThunderboltNet) |
| Fabric Routing | [plugins/fabricrouting.xml](plugins/fabricrouting.xml) | [FabricRouting](https://github.com/ibigsnet/FabricRouting) |
| NBD Export | [plugins/nbdexport.xml](plugins/nbdexport.xml) | [NbdExport](https://github.com/ibigsnet/NbdExport) |

Docker templates may return under `templates/` later.

## Layout

| Path | Purpose |
|------|---------|
| `ca_profile.xml` | CA repo profile |
| `plugins/*.xml` | Plugin wrappers (`PluginURL` → raw `.plg`) |
| `templates/` | Docker XMLs (empty for now) |
| `icon.png` | Repo icon |

Matches the [CA starter](https://github.com/unraid/unraid-community-apps-starter) layout.

## Production PluginURLs

CA wrappers point at each plugin’s **`stable`** branch (not `main`).  
`PluginURL` in the XML must **exactly** match the `.plg` `pluginURL` entity.

Maintainer notes: [RELEASE-CHANNEL.md](RELEASE-CHANNEL.md). Per-plugin safety notes: each source repo’s `SECURITY.md`.

## License

GNU GPLv3 or later — **ibigs, LLC** (Author: RifleJock). See [LICENSE](LICENSE).
