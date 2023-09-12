---
tags:
  - arch-linux
  - pentesting
  - hacking
---

Go to your `repos` directory and create a folder called `blackarch`, inside it get the file `https://blackarch.org/strap.sh`.
```bash
curl -O https://blackarch.org/strap.sh
```

Allow it to be executed
```bash
chmod +x strap.sh
```

And run it as root
```bash
sudo ./strap.sh
```

Check that BlackArch is up to date
```bash
sudo pacman -Sy
```

To install pentesting tools just use pacman.
```bash
sudo pacman -S BLACKARCH_TOOL
```