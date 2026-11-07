# Web Editor

Edit groups, players, ranks and permission nodes in your browser with drag & drop. Changes are applied to your server **instantly**.

## Opening the editor

1. Run `/ap editor` (requires `aether.admin`).
2. Click **"Click here to open the Web Editor"** in chat. From the console, the link is printed as plain text.
3. Start editing. The **● Live Sync Active** badge in the top bar shows you are connected.

## What you can do

- **Groups** (left panel): create groups, change weight, prefix/suffix and inheritance, see members, or delete a group.
- **Players** (right panel): search online and offline players, click one to edit their ranks, prefix and personal nodes.
- **Drag & drop:** drag a player onto a group to give them that rank. Hold **Shift** while dropping to make it their **only** rank.
- **Permission nodes:** add nodes with autocomplete from all your plugins, toggle true/false, set a world or a duration (`1d`, `2h30m`), or filter per plugin and search.
- **Chat preview:** see what a prefix/suffix looks like before saving.
- **Live activity:** a feed of every change, including changes made in-game or by other admins.

Several admins can work in the editor at the same time. Everyone sees each other's changes live.

## Security & privacy

- The link contains a **secret key after the `#`**. Browsers never send that part to any server.
- Everything between your server and your browser is **end-to-end encrypted** (AES-256-GCM). The relay at `editor.aetherdevstudio.com` only passes encrypted data along and cannot read or change your permissions.
- **Do not share the link.** Anyone with it has full permission access to your server for as long as the session is active.
- A session closes after **60 minutes of inactivity** (`web-editor.session-expiry-minutes`), when the server restarts, or when you click **Log out**. At most 5 sessions can be open per server; the oldest closes when you open a sixth.

## Network requirements

Your Minecraft server needs to reach `editor.aetherdevstudio.com` on port **443** (outgoing HTTPS/WebSocket). This works on virtually every host. You do **not** need to open any port, set up a domain or run a proxy.

## Self-hosted mode (advanced)

If your server has no internet access, or you want to host the editor yourself, switch to the built-in web server:

```yaml
web-editor:
  mode: SELF_HOSTED
  self-hosted:
    bind-address: "0.0.0.0"
    port: 8095
    public-url: "http://YOUR-SERVER-IP:8095/?token={token}"
    token-expiry-minutes: 10
```

- The port must be open in your firewall / host panel (on shared Minecraft hosts: add an extra port allocation and use that).
- This mode uses plain HTTP. For HTTPS, put a reverse proxy (Nginx, Caddy) or a Cloudflare Tunnel in front, set `bind-address: "127.0.0.1"` and change `public-url` to your HTTPS address.
- Links are single-use. Run `/ap editor` again for a new one.
- Apply changes with `/ap reload`.
