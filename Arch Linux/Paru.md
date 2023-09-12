Go into your `repos` directory and clone the repository `https://aur.archlinux.org/paru-bin.git`
```bash
git clone https://aur.archlinux.org/paru-bin.git
```

Then build the package
```bash
makepkg -si
```

To install a package you just use the command, without being root:
```bash
paru -S PACKAGE
```