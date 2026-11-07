# Network Setup (MySQL & multiple servers)

Share the same groups and player ranks across all servers in your network (lobby, survival, skyblock, …). A change on one server reaches the others within a few seconds.

## 1. Create a database

```sql
CREATE DATABASE aether CHARACTER SET utf8mb4;
CREATE USER 'aether'@'%' IDENTIFIED BY 'a-strong-password';
GRANT ALL PRIVILEGES ON aether.* TO 'aether'@'%';
FLUSH PRIVILEGES;
```

Most hosts let you create a database in their panel instead.

## 2. Configure every server

Use the same `storage` block on every server, and give each server its **own** `server-id`:

```yaml
server-id: "lobby"            # "survival", "skyblock", ... – unique per server!

storage:
  type: MYSQL
  mysql:
    host: "db.example.com"
    port: 3306
    database: "aether"
    username: "aether"
    password: "a-strong-password"
    use-ssl: false
  table-prefix: "aether_"

sync:
  poll-interval-seconds: 5
```

Restart each server. Tables are created automatically.

## How sync works

- An edit is applied **instantly** on the server where it was made.
- The other servers notice it within `poll-interval-seconds` and reload groups and online players automatically.
- This works the same for every kind of edit: commands, GUI, web editor and Vault.

## Per-server permissions

Permissions are shared network-wide. To limit something to one server, use the **world** context with that server's world name, e.g. `world=skyblock_world`, or use separate table prefixes for completely separate setups.

## Proxies (Velocity / BungeeCord)

Install AetherPermissions on each **backend Paper server**, not on the proxy.

## Tips

- Keep `maximum-pool-size` modest (5–10) per server. AetherPermissions uses very few queries, because everything is cached in memory.
- Make sure every server can reach the database host (firewall / allowed IPs).
