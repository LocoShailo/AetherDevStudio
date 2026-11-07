# AetherPermissions

**AetherPermissions** is a modern, visual permission plugin for **Paper 1.21+ (including 26.x)**. It is a drop-in alternative to LuckPerms with an in-game GUI, a hosted drag & drop web editor and instant live sync.

> This wiki is written for **server owners and server developers/admins** who install and configure the plugin.

## Highlights

| Feature | What it means for you |
|---|---|
| **Groups, weights & inheritance** | Build a rank ladder (`default` → `vip` → `mod` → `admin`) where higher ranks inherit lower ones. |
| **Temporary permissions & ranks** | Give `aether.fly` for 1 day or VIP for 30 days. It is removed automatically. |
| **Per-world permissions** | Grant or deny a node only in a specific world. |
| **In-game GUI** | `/ap gui`: manage everything from a chest menu. |
| **Hosted web editor** | `/ap editor`: edit groups and players in your browser. No open port or domain needed. |
| **Live sync** | Changes apply to online players instantly, without a reload. On MySQL they also sync across your whole network. |
| **Vault support** | Essentials, TAB, chat plugins and shops read ranks and prefixes automatically. |
| **SQLite or MySQL** | Zero-setup storage for single servers, MySQL for networks. |

## Pages

1. [[Installation|AetherPermissions-Installation]]
2. [[Commands & Permissions|AetherPermissions-Commands]]
3. [[Groups, Ranks & Permission Nodes|AetherPermissions-Groups-and-Permissions]]
4. [[Web Editor|AetherPermissions-Web-Editor]]
5. [[In-Game GUI|AetherPermissions-In-Game-GUI]]
6. [[Configuration (config.yml)|AetherPermissions-Configuration]]
7. [[Network Setup (MySQL & multiple servers)|AetherPermissions-Network-Setup]]
8. [[Vault, Chat & Plugin Integrations|AetherPermissions-Integrations]]
9. [[Troubleshooting & FAQ|AetherPermissions-Troubleshooting]]

## Quick start

```text
/ap group vip create 10
/ap group vip permission set essentials.fly
/ap group vip meta setprefix <gold>[VIP] 
/ap user Steve parent add vip
/ap editor
```

## Requirements

- Paper 1.21 or newer (26.x supported). Spigot is **not** supported.
- Java 21+
- Internet access on first start (to download the bundled libraries) and for the hosted web editor
- Optional: [Vault](https://www.spigotmc.org/resources/vault.34315/)
