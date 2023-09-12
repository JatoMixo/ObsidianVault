---
tags:
  - arch-linux
---
# [ArchWiki](https://wiki.archlinux.org/title/NetworkManager)
# Show available wifis
```bash
nmcli device wifi list
```

# Connect to a wifi
```bash
nmcli device connect WIFI_NAME password WIFI_PASSWORD
```
In case it's hidden:
```bash
nmcli device connect WIFI_NAME password WIFI_PASSWORD hidden yes
```
# Disconnect from a wifi
```bash
nmcli device disconnect ifname eth0
```
