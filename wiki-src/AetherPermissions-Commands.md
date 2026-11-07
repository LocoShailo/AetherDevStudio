# Commands & Permissions

Main command: **`/aetherperms`**, aliases **`/ap`** and **`/perms`**. Every command supports tab-completion, including permission nodes from all your installed plugins.

## General

| Command | Description |
|---|---|
| `/ap help` | Show all commands (click a command to paste it). |
| `/ap gui` | Open the [[in-game GUI|AetherPermissions-In-Game-GUI]]. |
| `/ap editor` | Create a [[web editor|AetherPermissions-Web-Editor]] session link. |
| `/ap reload` | Reload `config.yml` and force a full database sync. |
| `/ap groups` | List all groups, sorted by weight. |

## Users

| Command | Description |
|---|---|
| `/ap user <player> info` | Status, primary group, inherited groups, prefix/suffix and the player's own nodes. |
| `/ap user <player> permission set <node> [true\|false] [duration] [world=<world>]` | Set a node on the player. |
| `/ap user <player> permission unset <node> [world=<world>]` | Remove a node. |
| `/ap user <player> permission check <node>` | Show the *final* value after all groups are applied. |
| `/ap user <player> parent add <group> [duration] [world=<world>]` | Add a rank. |
| `/ap user <player> parent remove <group> [world=<world>]` | Remove a rank. |
| `/ap user <player> parent set <group> [duration]` | Remove all ranks, then add this one. |
| `/ap user <player> meta setprefix <text>` / `setsuffix <text>` | Personal prefix/suffix (overrides the group's). |
| `/ap user <player> meta clearprefix` / `clearsuffix` | Go back to the group prefix/suffix. |

Players don't need to be online. Offline players are looked up in the database.

## Groups

| Command | Description |
|---|---|
| `/ap group <group> create [weight]` | Create a group (names: `a-z 0-9 _ -`, max 36 characters). |
| `/ap group <group> delete` | Delete a group and remove it from every player and group. The default group cannot be deleted. |
| `/ap group <group> info` | Weight, prefix/suffix, inherited groups and nodes. |
| `/ap group <group> setweight <weight>` | Change the priority. |
| `/ap group <group> permission set\|unset\|check ...` | Same syntax as for users. |
| `/ap group <group> parent add\|remove <group>` | Make this group inherit (or stop inheriting) another group. |
| `/ap group <group> meta setprefix\|setsuffix <text>` | Group prefix/suffix. |
| `/ap group <group> meta clearprefix\|clearsuffix` | Remove the prefix/suffix. |

## Optional arguments

The `[true|false] [duration] [world=<world>]` arguments can be given in any order:

```text
/ap user Steve permission set aether.fly true 1d world=world_nether
/ap group vip permission set essentials.nick false
/ap user Alex parent add vip 2w
```

**Durations:** `30s`, `10m`, `2h`, `1d`, `1w`, `1mo`, and combinations like `1d12h` or `2h30m`.

## Plugin permissions

| Permission | Default | Grants |
|---|---|---|
| `aether.admin` | OP | Everything, including `/ap gui`, `/ap editor` and `/ap reload`. |
| `aether.command.user` | OP | All `/ap user ...` commands. |
| `aether.command.group` | OP | All `/ap group ...` commands. |
| `aether.command.info` | OP | `/ap groups`. |

> ⚠️ Anyone with `aether.command.user` or `aether.command.group` can give themselves any permission. Treat these like `aether.admin`.
