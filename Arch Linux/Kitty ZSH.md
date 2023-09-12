---
tags:
  - arch-linux
  - terminal
  - shell
---
# [Arch Linux Fonts](https://wiki.archlinux.org/title/fonts)
# Kitty
Install it with pacman.
```bash
sudo pacman -S kitty
```

If you want to customize it, edit [`~/.config/kitty/kitty.conf`](https://sw.kovidgoyal.net/kitty/conf/).

# ZSH
To install it just use.
```bash
sudo pacman -S zsh
```

If you want to customize it, edit `~/.zshrc`.
# Install Cascadia Code Nerd Font
```bash
sudo pacman -S ttf-cascadia-code
```
# ZSH Plugins
Install the following using paru:
- `zsh-autosuggestions`: For ZSH autosuggestions
- `zsh-syntax-highlighting`: For ZSH Coloring and syntax highlighting
```bash
paru -S zsh-autosuggestions zsh-syntax-highlighting
```

To use ZSH-Sudo plugin, you'll need to download the plugin from OhMyZsh.
```bash
# As root
cd /usr/share
mkdir zsh-sudo

chown USER:USER zsh-sudo

exit
cd /usr/share/zsh-sudo

wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/plugins/sudo/sudo.plugin.zsh
```

# [Powerlevel10K](https://github.com/romkatv/powerlevel10k)
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
```

Then use the following command to customize it.
```bash
p10k configure
```
# [Starship](https://starship.rs/)