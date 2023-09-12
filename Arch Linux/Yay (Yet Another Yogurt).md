Go into your `repos` directory and clone the repository `https://aur.archlinux.org/yay.git`.
```bash
git clone https://aur.archlinux.org/yay.git
```

Then build the package.
```bash
makepkg -si
```

To install packages just use the command
```bash
sudo yay -S PACKAGE
```