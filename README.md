# Super Apps

Tap the **Super** key by itself and get a searchable grid of every installed
app — press it again (or Escape / click outside) to close. Start typing to
filter, use the arrow keys and Enter, or click an icon to launch it.

It's an [Omarchy](https://omarchy.org/) Quattro shell plugin: a fullscreen
overlay that reuses Omarchy's own app library, so it shares the same icons,
launch behavior, and menu theming as the built-in Apps menu — just bound to
a single key.



<img width="2560" height="1440" alt="image" src="https://github.com/user-attachments/assets/2bdb42ee-cd68-4f32-b81c-8adfde82f6cc" />



## Install

```
omarchy plugin add https://github.com/younesdahdouh/omarchy-super-apps.git --enable
```

Or clone manually into `~/.config/omarchy/plugins/`:

```
git clone https://github.com/younesdahdouh/omarchy-super-apps.git \
  ~/.config/omarchy/plugins/io.github.younesdahdouh.super-apps
omarchy plugin enable io.github.younesdahdouh.super-apps
```

## Bind it to the Super key

Add this to `~/.config/hypr/bindings.lua`:

```lua
o.bind("SUPER + SUPER_L", "All apps", "omarchy-shell shell toggle io.github.younesdahdouh.super-apps", { release = true })
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
instead, e.g. `SUPER + SPACE`:

```
o.bind("SUPER + SPACE", "All apps", "omarchy-shell shell toggle io.github.younesdahdouh.super-apps")
```

You can always trigger it by hand too:

```
omarchy-shell shell toggle io.github.younesdahdouh.super-apps
```

## Uninstall

```
omarchy plugin remove io.github.younesdahdouh.super-apps
```

Then remove the binding you added to `~/.config/hypr/bindings.lua`.

## License

MIT — see [LICENSE](LICENSE).
