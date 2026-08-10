# Noctalia-backup

Config backup for a [niri](https://github.com/YaLTeR/niri) desktop running [noctalia-shell](https://docs.noctalia.dev). Saved so the setup can be rebuilt from scratch without redoing every setting by hand.

## Contents

| File | Goes to | What it is |
| --- | --- | --- |
| `settings.json` | `~/.config/noctalia/` | The full noctalia-shell settings dump (`settingsVersion` 59): app launcher, bar, dock, control center, notifications, OSD, night light, wallpaper, color schemes, session menu, system monitor, and desktop widgets. |
| `keybinds.kdl` | included from `~/.config/niri/config.kdl` | niri key bindings. Application launches (Alacritty, Firefox) plus the noctalia bindings, which are driven over IPC, for example `qs -c noctalia-shell ipc call launcher toggle`. Each bind carries a `hotkey-overlay-title` so it reads properly in niri's hotkey overlay. |
| `rules1.kdl` | included from `~/.config/niri/config.kdl` | Window rules and the compositor blur block: 3 passes, offset 3.5, noise 0.02, saturation 1.7, with 20px corner radius and clip-to-geometry on all windows. Tuned so the wallpaper still reads through the blur instead of being flattened. |
| `fastfetchnew.jsonc` | `~/.config/fastfetch/` | fastfetch config. |

## Requirements

niri, Quickshell, and noctalia-shell. The keybinds also assume Alacritty and Firefox are installed; the file leaves the file-manager bind unset on purpose.

## Before you use it

`settings.json`, `fastfetchnew.jsonc`, and parts of the keybinds reference absolute paths under `/home/sannur` (wallpapers, avatar, logo). Update those to your own home directory or the shell will fall back to defaults.

Clipboard history is disabled in this dump while the `wl-paste ... cliphist store` watch commands are still configured, so turn `enableClipboardHistory` on if you want it.

## Caveats

Single upload from May 2026, kept as a restore point rather than a maintained config. `settingsVersion` 59 may not match current noctalia-shell; newer versions will migrate it, older ones may not read it.

## License

GPL-3.0. `keybinds.kdl` and `rules1.kdl` are copies of the config CachyOS ships in
[cachyos-niri-noctalia](https://github.com/CachyOS/cachyos-niri-noctalia), which is
GPL-3.0, so this repo inherits it. [NOTICE](NOTICE) lists what came from where.
