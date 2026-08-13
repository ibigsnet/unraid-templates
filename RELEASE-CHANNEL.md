# Maintainer notes (not user-facing)

CA submit: https://ca.unraid.net/submit — repo  
`https://github.com/ibigsnet/unraid-templates`

| Path | Role |
|------|------|
| `ca_profile.xml` | CA profile |
| `plugins/*.xml` | Plugin wrappers; `PluginURL` → raw `.plg` on **stable** |
| `templates/` | Docker XMLs (empty) |

`PluginURL` must exactly match each plugin’s stable `.plg` `pluginURL` entity.

| Branch (plugin repos) | Role |
|----------------------|------|
| `main` | Lab / development |
| `stable` | CA / production |

Ship: test on `main` → point entities at `stable` → push `main` + `stable`.  
Version rules: each plugin `RELEASES.md`.
