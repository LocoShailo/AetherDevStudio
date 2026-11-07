# Installation

## 1. Install the jar

1. Stop your server.
2. Put `AetherPermissions-x.x.x.jar` in your `plugins/` folder.
3. *(Recommended)* Install **Vault** so other plugins can read ranks and prefixes.
4. **Remove any other permission plugin** (LuckPerms, GroupManager, PermissionsEx, …). Two permission plugins at the same time will fight over player permissions.
5. Start the server.

On the first start Paper downloads the libraries AetherPermissions needs (database drivers, connection pool, cache) from Maven Central. This happens once and needs an internet connection.

You should see this in the console:

```text
[AetherPermissions] Storage: SQLITE – 1 groups loaded.
[AetherPermissions] Hooked into Vault (Permission + Chat).
[AetherPermissions] Web Editor: hosted relay mode (https://editor.aetherdevstudio.com/)
[AetherPermissions] AetherPermissions enabled. Live Sync Active.
```

## 2. Give yourself access

All management commands require `aether.admin`, which OPs have by default. From the console you can grant it to a non-OP player:

```text
ap user YourName permission set aether.admin
```

## 3. Build your ranks

A typical setup:

```text
/ap group default permission set essentials.home
/ap group vip create 10
/ap group vip parent add default
/ap group vip meta setprefix <gold>[VIP] 
/ap group mod create 50
/ap group mod parent add vip
/ap group admin create 100
/ap group admin parent add mod
/ap group admin permission set *
```

Or do it all visually with `/ap editor` or `/ap gui`.

## 4. Assign players

```text
/ap user Steve parent add vip          # permanent
/ap user Alex parent add vip 30d       # 30 days
/ap user Notch parent set admin        # removes all other ranks first
```

## Updating

1. Stop the server.
2. Replace the jar.
3. Start the server.

Your data (in `aether.db` or MySQL) and your `config.yml` are kept. New config options are documented on the [[Configuration|AetherPermissions-Configuration]] page.

## Uninstalling

Remove the jar. Your data stays in `plugins/AetherPermissions/` (SQLite) or in your MySQL database.
