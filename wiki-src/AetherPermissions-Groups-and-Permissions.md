# Groups, Ranks & Permission Nodes

## The default group

Every player is **always** in the default group (`default-group` in config, `default` out of the box). You never need to add players to it. Put the permissions every player should have here.

## Weight

Every group has a **weight** (a number). A higher weight means a higher priority:

- When two groups set the **same node differently**, the group with the higher weight wins.
- The player's **primary group** is the group with the highest weight they have (directly or inherited). Vault reports this group to other plugins.
- The **prefix/suffix** comes from the highest-weight group that has one.

Recommended spacing: `default 0`, `vip 10`, `mvp 20`, `helper 40`, `mod 50`, `admin 100`. This leaves room to add ranks in between later.

## Inheritance

```text
/ap group vip parent add default
/ap group mod parent add vip
```

`mod` now has everything `vip` and `default` have. Inheritance can go multiple levels deep. Loops are blocked: you cannot make `default` inherit `mod` if `mod` already inherits `default`.

## How the final permission is decided

For each node, AetherPermissions applies these sources in order; **later sources override earlier ones**:

1. All of the player's groups, from **lowest weight to highest weight**.
2. The player's **own nodes** (set with `/ap user ... permission set`). They override every group.

Within one group or player, a **world-specific** node overrides the **global** one.

Use `/ap user <player> permission check <node>` to see the final value.

## Negating (false) nodes

Setting a node to `false` explicitly **denies** it, even if a lower group grants it:

```text
/ap group default permission set essentials.fly
/ap group muted permission set essentials.fly false
```

## Temporary permissions & ranks

Add a duration to any node or rank:

```text
/ap user Steve permission set aether.fly 1d
/ap user Alex parent add vip 30d
```

Expired entries are removed automatically within a few seconds (configurable), and online players are told when a temporary permission expires. The GUI and web editor show the remaining time.

## Per-world permissions

```text
/ap group default permission set worldedit.wand world=creative
/ap user Steve parent add builder world=creative
```

The node or rank only applies while the player is in that world. Permissions update instantly when the player changes world.

## Wildcards

| Node | Matches |
|---|---|
| `essentials.*` | Every registered permission that starts with `essentials.` |
| `*` | Every registered permission on the server |

A more specific wildcard wins over a less specific one, and an explicitly set node always wins over a wildcard. Wildcards only expand to permissions that plugins **register** (in their `plugin.yml` or in code). This is the same as how LuckPerms behaves on Paper.

## Prefixes & suffixes

Both **MiniMessage** and **legacy `&` codes** work:

```text
/ap group vip meta setprefix <gradient:#FFD700:#FFA500>[VIP]</gradient> 
/ap group mvp meta setprefix &b&l[MVP] 
```

Remember the trailing space if you want space between the prefix and the name. A player's personal prefix (`/ap user <player> meta setprefix`) overrides their group prefix.

## Group membership is also a node

Ranks are stored as `group.<name>` nodes, so these two commands do the same thing:

```text
/ap user Steve parent add vip
/ap user Steve permission set group.vip
```

Other plugins can check `player.hasPermission("group.vip")`. It is `true` for every group the player has, including inherited ones.
