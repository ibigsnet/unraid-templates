# Release channel

| Branch (plugin repos) | Role |
|----------------------|------|
| `main` | Development / lab |
| `stable` | CA / production |

This repo’s `plugins/*.xml` use **stable** PluginURLs only.  
`PluginURL` must match the `.plg` `pluginURL` entity exactly.

## Ship

1. Test from `main` on lab.
2. Bump version; point `pluginURL` / `raw` at **stable**.
3. Push `main` and fast-forward `stable`.

Version rules: each plugin `RELEASES.md` (fleet `YYYY.MM.DD` + two-letter suffixes).
