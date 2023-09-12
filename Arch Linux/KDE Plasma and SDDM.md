---
tags:
  - arch-linux
---
# [Wiki](https://wiki.archlinux.org/title/KDE)
KDE Plasma is just a desktop environment with window manager and SDDM is a display manager with login system.
# Installation
There are several packages you can install to have Plasma working
- `plasma`: it's a group containing the desktop environment and other applications developed by KDE.
- `plasma-desktop`: a minimal desktop environment working with X11 (xorg).
- `plasma-wayland-session`: to have wayland working for plasma. If you're using the propietary `nvidia` driver you will also need to enable `DRM Kernel Mode settings` following the guide on the wiki.
```bash
sudo pacman -S plasma-desktop
```

You will also need to install `sddm` in case it didn't get installed with Plasma.
```bash
sudo pacman -S sddm
```

Now, just enable the `sddm` service and reboot the system.
```bash
sudo systemctl enable sddm
```
# Resolution
To change the resolution of `SDDM` you need to modify `/usr/share/sddm/scripts/Xsetup` by adding the following line at the bottom.
```
xrandr --output OUTPUT --mode RESOLUTION
```

Of course changing `OUTPUT` to your output and `RESOLUTION` to the wanted resolution.

# SDDM Theme
You will need to install a package `sddm-kcm` to be able to customize the sddm theme from Plasma.
```bash
sudo pacman -S sddm-kcm
```

Now go into `System Settings > Startup and Shutdown > Login Screen (SDDM)` and select the theme you want, you can also change the background of SDDM from there.

If you want to apply the dark theme, you will need to hit `Apply Plasma Settings`.
# Keyboard layout
KDE Plasma uses its own configured keyboard layout, to change it go into `System Settings > Input Devices > Keyboard > Layouts`, enable `Configure layouts` and add the ones you want.
# Background
You can use `feh` to set the background.
```bash
sudo pacman -S feh # Install it

feh --bg-scale PATH/TO/BACKGROUND
```