# Troubleshooting & FAQ

## "Could not reach the web editor service"

Your server cannot connect to `editor.aetherdevstudio.com`.

- Check that the server has internet access and that outgoing port **443** is not blocked.
- Try again after a minute (short network hiccups).
- No internet on the server? Use [[self-hosted mode|AetherPermissions-Web-Editor]].

## The web editor says "session expired" or "server disconnected"

Sessions close after inactivity, on a server restart or when the server loses its connection. Run `/ap editor` again for a new link.

## Prefixes don't show up in chat / tab

1. Is **Vault** installed? Check the console for `Hooked into Vault`.
2. Does your chat/tab plugin use Vault for prefixes? (EssentialsX Chat and TAB do.)
3. Does the player's highest-weight group actually have a prefix? Check with `/ap user <player> info`.
4. No chat plugin at all? Enable `chat.format-enabled`.

## A permission doesn't work

1. Run `/ap user <player> permission check <node>` to see the final value.
2. Look for a higher-weight group, or a personal node, that sets it to `false`.
3. Check whether the node is world-specific (`world=...`).
4. Wildcard not working? The plugin must **register** the permission. Set the exact node instead.
5. Make sure no other permission plugin (e.g. LuckPerms) is installed.

## Players are kicked with "Your permission data could not be loaded"

The database could not be reached while they joined. Check the MySQL connection details and that the database server is online. The console shows the exact error.

## Changed `config.yml` but nothing happened

Run `/ap reload`. Changing `storage` settings needs a full restart.

## The plugin doesn't start: missing classes / "NoClassDefFoundError"

On first start the server must download libraries from Maven Central. Make sure it has internet access, then restart.

## FAQ

**Does it work on Spigot?** No, Paper (or a Paper fork like Purpur) 1.21+ is required.

**Does it work on 26.x?** Yes.

**Can I import my LuckPerms data?** There is no automatic importer yet. Recreate your groups in the web editor; with drag & drop this is quick.

**Is the web editor safe?** Yes. Traffic is end-to-end encrypted and the relay cannot read it. Just never share the link.

**Does it cause lag?** No. Permissions are calculated in advance and cached per player, so permission checks are instant. Database writes happen in the background.

**Can several admins edit at the same time?** Yes, in the GUI and in the web editor. Everyone sees changes live.

**Where is my data stored?** In `plugins/AetherPermissions/aether.db` (SQLite) or in your MySQL database. Back up that file or database regularly.
