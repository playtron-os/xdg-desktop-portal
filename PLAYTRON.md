# Playtron's xdg-desktop-portal

Kora builds xdg-desktop-portal from this fork. Each `playtron/<version>` branch is an
upstream release tag plus the commits below, and is tagged `<version>-playtron.<n>`.

## What it carries

- **Find desktop files GLib has not noticed yet** (`fix(app-info): …`). GLib rereads an
  applications folder only when a file monitor on it fires. On Kora that folder is reached
  through a Nix profile symlink, and installing an app from Discover replaces the symlink,
  so no monitor fires and the portal refuses to register the new app until it restarts.
  Upstream declined the fix
  ([flatpak/xdg-desktop-portal#2189](https://github.com/flatpak/xdg-desktop-portal/pull/2189)).

## Moving to a new release

Branch `playtron/<version>` from the upstream tag, cherry-pick the commits above, check
`meson test` passes, push, and tag `<version>-playtron.1`. Drop the fork when upstream or
GLib fixes the watch.
