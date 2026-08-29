# Super Apps

Tap the **Super** key by itself and get a searchable grid of every installed
app — press it again (or Escape / click outside) to close. Start typing to
filter, use the arrow keys, Page Up/Down, and Enter, or click an icon to
launch it.

It's an [Omarchy](https://omarchy.org/) Quattro shell plugin: a fullscreen
overlay that reuses Omarchy's own app library, so it shares the same icons,
launch behavior, and menu theming as the built-in Apps menu — just bound to
a single key.


<p align="center">
<img width="727" height="604" alt="screenshot-2026-08-28_22-28-51" src="https://github.com/user-attachments/assets/b0934931-3c15-425c-96b4-a0f0cd69998b" />



## Install

```
omarchy plugin add https://github.com/younesdahdouh/omarchy-super-apps.git --enable
```

Or clone manually into `~/.config/omarchy/plugins/`:

```
git clone https://github.com/younesdahdouh/omarchy-super-apps.git \
  ~/.config/omarchy/plugins/super-apps
omarchy plugin enable super-apps
```

## Bind it to the Super key

Add this to `~/.config/hypr/bindings.lua`:

```lua
o.bind("SUPER + SUPER_L", "All apps", "omarchy-shell shell toggle super-apps", { release = true })
```

`{ release = true }` is the same option Omarchy's own push-to-talk binding
uses (see `omarchy-launch-or-focus` / voxtype's `F9` binding) — it fires the
command on key-up instead of key-down, which is what makes a bare tap of
Super work as a toggle.

**Known Hyprland quirk:** a release-bind on a modifier key fires whenever
*any* Super press-and-release ends — including after `SUPER + 1` or
`SUPER + TAB` — not only a standalone tap. This is standard behavior for
"press Super to open the launcher" setups on Hyprland; it can pop the grid
open right after a workspace switch. If that bothers you, bind a combo
instead or another key like TAB instead.

```lua
o.bind("CTRL + TAB", "All apps", "omarchy-shell shell toggle super-apps", { release = true })
```
You can always trigger it by hand too:

```
omarchy-shell shell toggle super-apps
```
## Uninstalling an app from the grid

Select an app and press **Delete**. You'll get a confirmation prompt —
"Do you want to uninstall X?" — before anything happens; Escape or clicking
Cancel backs out with no changes.

This is a real uninstall, not just hiding the icon: confirming runs
`omarchy-remove-launcher-entry`, the same sudo-gated helper the built-in
Omarchy menu's own Apps submenu uses when you delete an app from there, so
it may prompt for your password. It's exactly the native menu's own
delete flow, just reachable from this grid too.

<p align="center">
<img width="1030" height="900" alt="screenshot-2026-08-28_22-30-22" src="https://github.com/user-attachments/assets/de7dca0f-bea6-47f2-918e-624138e7971d" />



## Uninstall

```
omarchy plugin remove super-apps
```

Then remove the binding you added to `~/.config/hypr/bindings.lua`.

## License

MIT — see [LICENSE](LICENSE).
