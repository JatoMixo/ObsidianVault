---
tags:
  - neovim
---
# Installation
```bash
sudo pacman -S neovim
```
# Configuration
To configure it you will have to edit `.config/nvim`.

# [Packer](https://github.com/wbthomason/packer.nvim)
To install it just use:
```bash
git clone --depth 1 https://github.com/wbthomason/packer.nvim\
 ~/.local/share/nvim/site/pack/packer/start/packer.nvim
```

Then load your configuration and use `:PackerSync` command.