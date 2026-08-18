# CA channel

All `plugins/*.xml` **PluginURL** values must use each project’s **`stable`** branch raw `.plg`.

| Wrong | Right |
|-------|--------|
| `…/ThunderboltNet/main/thunderboltnet.plg` | `…/ThunderboltNet/stable/thunderboltnet.plg` |
| `…/StorageGuard/main/…` | `…/StorageGuard/stable/…` |

CA AppFeed scrapes this repo. After changing PluginURL, wait for feed refresh (or CA “Force Update”) before trusting the Apps card “Current Version”.

Production freeze (Thunderbolt Net): **2026.08.17an** until an explicit stable promote.
