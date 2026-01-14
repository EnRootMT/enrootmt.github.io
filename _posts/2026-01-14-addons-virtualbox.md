
---
title: Activer le copier coller entre machine hôte et VM Ubuntu
date: 2026-01-14
categories: [Tutoriels, Linux]
tags: [ubuntu, virtualbox, vm]
---

# Installer les Additions invité VirtualBox sous Ubuntu

```bash
sudo apt update
sudo apt install build-essential dkms linux-headers-$(uname -r)
sudo sh /media/*/VBox*/VBoxLinuxAdditions.run
sudo reboot
```

# Activer l'option


