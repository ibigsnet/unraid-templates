# Release channel policy

## Branches

| Branch | Purpose | PluginURL / raw |
|--------|---------|-----------------|
| `main` | Lab + active development | `…/main/…` |
| `stable` | CA / end users / production | `…/stable/…` |

## PluginURL rule

**On the branch that is checked out / shipped, entities must match that branch:**

```xml
<!-- on main -->
<!ENTITY pluginURL "https://raw.githubusercontent.com/ibigsnet/REPO/main/FILE.plg">
<!ENTITY raw "https://raw.githubusercontent.com/ibigsnet/REPO/main">

<!-- on stable -->
<!ENTITY pluginURL "https://raw.githubusercontent.com/ibigsnet/REPO/stable/FILE.plg">
<!ENTITY raw "https://raw.githubusercontent.com/ibigsnet/REPO/stable">
```

CA wrappers in `unraid-templates` always use **stable** PluginURLs.

## Lab workflow (preferred for our plugins)

1. **Uninstall** from Unraid (Plugins → Remove), not only “Update”.
2. **Sanity check** leftovers (paths below).
3. **Install from main** raw URL (lab only).
4. Test. Document concerns in private `.grok-notes/` or a lab log.
5. When ready to ship: merge to `stable`, rewrite entities to `stable`, bump version, push `stable`.

### Why uninstall → reinstall for lab (not only Update)

| Path | Pros | Cons |
|------|------|------|
| Update plugin | Fast | Skips full remove; can hide uninstall bugs, stale files, dual plg names |
| Uninstall → install | Exercises remove + cold install | Brief feature gap; need leftover checklist |

**Lab default: uninstall → sanity → install from `main`.**  
**Production/CA users: stay on Update from `stable`.**

### Leftover checklist (after uninstall)

```bash
# emhttp
ls -la /usr/local/emhttp/plugins/ | grep -iE 'storageguard|thunderbolt|fabric|nbd|unraidfrr'
# flash
ls -la /boot/config/plugins/ | grep -iE 'storageguard|thunderbolt|fabric|nbd|unraidfrr|tbn-'
# plg registry
ls /boot/config/plugins/*.plg /var/log/plugins/*.plg 2>/dev/null | grep -iE 'storage|thunder|fabric|nbd|unraidfrr|tbn-'
# FRR packages (only if Fabric Routing was installed)
ls /var/log/packages/ 2>/dev/null | grep -iE 'frr|libyang' || true
# NBD runtime
ls /var/run/nbdexport 2>/dev/null; pgrep -a qemu-nbd || true
# StorageGuard inject
grep -n storageguard /usr/local/emhttp/webGui/include/DefaultPageLayout/HeadInlineJS.php 2>/dev/null || echo "SG inject: clean"
```

### Lab install URLs (main)

```text
https://raw.githubusercontent.com/ibigsnet/StorageGuard/main/storageguard.plg
https://raw.githubusercontent.com/ibigsnet/ThunderboltNet/main/thunderboltnet.plg
https://raw.githubusercontent.com/ibigsnet/FabricRouting/main/fabricrouting.plg
https://raw.githubusercontent.com/ibigsnet/NbdExport/main/install.plg
```

## Ship checklist (production)

1. Tested on lab via main uninstall/reinstall path.
2. Bump version; rewrite `pluginURL` + `raw` (+ FRR catalog) to **stable**.
3. Merge/push `main`, fast-forward `stable`, push `stable`.
4. Confirm CA XML PluginURL matches stable entity.
5. Do **not** leave a higher version only on main.

## Existing installs that still point at old main URLs

After the stable cutover, lab reinstall from main (this channel) is the cleanest reset.
