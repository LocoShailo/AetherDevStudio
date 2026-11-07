# In-Game GUI

Open it with **`/ap gui`** (requires `aether.admin`). Everything you change applies instantly, and open menus refresh live when someone else (another admin, the web editor or the console) changes something.

## Main menu

| Button | Opens |
|---|---|
| **Manage Groups** | List of all groups, sorted by weight. |
| **Manage Players** | Online players first, then all known players (searchable). |
| **Web Editor** | Generates a web editor link in chat. |
| **Live Sync** | Status: storage type, cached users, known permissions. |
| **Your Permissions** | Your own player profile. |
| **Reload & Sync** | Same as `/ap reload`. |

## Groups

- **Left-click** a group to edit it, **Shift + Right-click** to delete it (with confirmation).
- **+ Create Group**: type a name in chat, optionally followed by a weight (e.g. `vip 10`).

In the group editor:

| Item | Action |
|---|---|
| **Permission Nodes** | Opens the node list (see below). |
| **Inheritance** | Click groups to toggle inheritance (loops are blocked). |
| **Weight** | Left/Right-click `+1/-1`, Shift-click `+10/-10`, press **Q** (drop key) to type an exact value. |
| **Prefix & Suffix** | Left-click: set prefix, Right-click: set suffix, Shift + Right-click: clear both. |
| **Delete Group** | Deletes the group (not available for the default group). |

## Players

Click a player to open their profile:

- **Groups / Ranks**: click to add or remove a rank, **Shift-click** to add it temporarily (you'll be asked for a duration).
- **Personal Permissions**: nodes that override all groups.
- **Personal Prefix & Suffix**: Shift + Right-click resets back to the group's prefix/suffix.

## Node list

| Click | Action |
|---|---|
| Left-click | Toggle true / false |
| Shift + Left-click | Set a duration (or type `permanent`) |
| Right-click | Remove the node |

Buttons at the bottom:

- **+ Add Node**: type e.g. `essentials.fly true 1d world=world_nether`.
- **Browse Permissions**: pick nodes from every installed plugin, grouped per plugin. Left-click = grant, Right-click = deny, Shift + Right-click = remove. Each plugin also offers a `plugin.*` wildcard shortcut.
- **Filter** (hopper): cycle through categories/plugins. Shift-click shows all.
- **Search**: type part of a node name. Shift-click clears the search.

Icons: 🟢 lime dye = granted, 🔴 red dye = denied, 🕒 clock = temporary.

## Typing input

When the GUI needs text (a name, node, weight or prefix), the menu closes and you type your answer in chat. Your message is **not** shown to other players. Type `cancel` to go back without changing anything.
