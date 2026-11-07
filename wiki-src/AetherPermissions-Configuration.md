# Configuration (`config.yml`)

File: `plugins/AetherPermissions/config.yml`. Apply changes with **`/ap reload`**. A few options (marked ⟳) need a **full restart**.

## General

| Option | Default | Description |
|---|---|---|
| `server-id` | `survival-1` | Unique name of this server. Must be **different on every server** that shares a MySQL database. |
| `default-group` | `default` | Group every player always has. Created automatically. |
| `wildcards` | `true` | Expand `plugin.*` and `*` nodes. |
| `messages.prefix` | gradient "Aether »" | Chat prefix for plugin messages (MiniMessage). |

## Storage ⟳

```yaml
storage:
  type: SQLITE            # SQLITE or MYSQL
  sqlite-file: "aether.db"
  mysql:
    host: "localhost"
    port: 3306
    database: "aether"
    username: "root"
    password: ""
    use-ssl: false
  pool:
    maximum-pool-size: 10
    minimum-idle: 2
    connection-timeout-ms: 5000
    max-lifetime-ms: 1800000
  table-prefix: "aether_"
```

- **SQLITE**: a single file in the plugin folder. Best for a single server.
- **MYSQL** (also works with MariaDB): required if several servers should share permissions. See [[Network Setup|AetherPermissions-Network-Setup]].
- `table-prefix`: lets several plugins or servers share one database without table name clashes.
- Changing the storage type does **not** copy your data. Set up your ranks again (the web editor makes that quick).

## Sync

```yaml
sync:
  poll-interval-seconds: 5    # check for changes made by OTHER servers (MySQL); 0 = off
  expiry-check-seconds: 5     # how often expired temporary nodes are removed
```

Changes made on the same server are always applied instantly. These settings only control cross-server polling and expiry.

## Web editor

```yaml
web-editor:
  enabled: true
  mode: RELAY                    # RELAY (hosted, recommended) or SELF_HOSTED
  session-expiry-minutes: 60
  relay:
    editor-url: "https://editor.aetherdevstudio.com/"
    socket-url: "wss://editor.aetherdevstudio.com/ws"
  self-hosted:
    bind-address: "0.0.0.0"
    port: 8095
    public-url: "http://your-server-ip:8095/?token={token}"
    token-expiry-minutes: 10
```

Leave the `relay` URLs as they are. See [[Web Editor|AetherPermissions-Web-Editor]] for both modes.

## Chat formatting

```yaml
chat:
  format-enabled: false
  format: "<prefix><white><name></white><suffix> <dark_gray>»</dark_gray> <gray><message>"
```

Turn this on if you have **no** chat plugin and want ranks shown in chat. Placeholders: `<prefix>`, `<suffix>`, `<name>`, `<message>`. Leave it `false` when you use EssentialsX Chat, VentureChat, etc.; they get the prefix through Vault.
