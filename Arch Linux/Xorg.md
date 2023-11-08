---
tags:
  - arch-linux
---
It is an open source display server commonly used in several Linux distros.
# [Wiki](https://wiki.archlinux.org/title/Xorg)
# Installation
Easiest way to install it is with the group `xorg`.
```bash
sudo pacman -S xorg xorg-server xorg-xinit
```

Then you can install the corresponding driver for your GPU.
```bash
sudo pacman -S xf86-video OTHER_DRIVER_FROM_WIKI
```
# Xrandr
It comes installed with xorg.

To show the output devices and resolutions available just use
```bash
xrandr
```

And to change your resolution or your display
```bash
xrandr --output HDMI-1 --mode 1920x1080 --rate 60 # Rate is optional
```