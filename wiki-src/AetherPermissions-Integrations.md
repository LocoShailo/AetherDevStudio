# Vault, Chat & Plugin Integrations

## Vault

With [Vault](https://www.spigotmc.org/resources/vault.34315/) installed, AetherPermissions registers itself as the **Permission** and **Chat** provider. Plugins that use Vault then work automatically:

| Plugin type | Examples | What they get |
|---|---|---|
| Essentials | EssentialsX, EssentialsX Chat | Ranks, prefix/suffix, group-based settings |
| Tab / scoreboard | TAB, Tablist plugins | Prefix/suffix and group for sorting |
| Chat plugins | VentureChat, ChatControl, DeluxeChat | Prefix/suffix |
| Shops & ranks | Rank-up plugins, shop plugins | Add/remove ranks, check groups |

Check the console on startup for `Hooked into Vault (Permission + Chat).`

### Details

- **Primary group** = the player's highest-weight group.
- **Prefix/suffix** are sent as classic colour codes, so every plugin can show them. MiniMessage gradients and hex colours are converted automatically.
- Plugins that **add or remove ranks** through Vault (e.g. a rank-up plugin) go through AetherPermissions, are saved and synced like any other change.
- Vault **meta/info** values are stored as nodes named `meta.<key>.<value>`. For example, `meta.homes.5` returns `5` for the key `homes`.

## Plugins without Vault

Plugins that only check `player.hasPermission(...)` work automatically. AetherPermissions sets the permissions directly on the player, the standard Paper way.

## PlaceholderAPI

Use the Vault expansion:

```text
/papi ecloud download Vault
/papi reload
```

Placeholders: `%vault_prefix%`, `%vault_suffix%`, `%vault_group%`, `%vault_rank%`.

## Built-in chat format

No chat plugin? Enable `chat.format-enabled` in the [[Configuration|AetherPermissions-Configuration]] to show prefixes in chat.

## Group checks in other plugins

Every group a player has (including inherited ones) is available as the permission `group.<name>`. For example, a plugin or config can require `group.vip`.
