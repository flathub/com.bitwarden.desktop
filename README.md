# The flatpak manifest for Bitwarden Desktop

Please point issues with the flatpak release to https://github.com/bitwarden/clients/issues.

## Experimental Wayland support

Electron (the technology used to build the Bitwarden Desktop app) may not play nicely with Wayland at the current moment, especially in GNOME.
Regardless, you have the ability to try out Wayland by setting the environment variable `ELECTRON_OZONE_PLATFORM_HINT=auto` and giving access to the Wayland socket.

```sh
flatpak override --user --env=ELECTRON_OZONE_PLATFORM_HINT=auto com.bitwarden.desktop
flatpak override --user --socket=wayland com.bitwarden.desktop
```

When using Wayland, it is also safe to disable X11 and IPC access from the Flatpak sandbox.

```sh
flatpak override --user --nosocket=x11 com.bitwarden.desktop
flatpak override --user --unshare=ipc com.bitwarden.desktop
```

You can also use [Flatseal](https://flathub.org/apps/com.github.tchx84.Flatseal) to manage these via a GUI.
