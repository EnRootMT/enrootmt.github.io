
---
title: Activer le copier coller entre machine hôte et VM Ubuntu
date: 2026-01-14
categories: [Tutoriels, Linux]
tags: [ubuntu, virtualbox, vm]
---

* Inserer le cd des addons

![My image](/_assets/img/Screenshot_20260114_101706-1.png)


![insert CD](https://enrootmauvaisetroupe.fr/wp-content/uploads/2022/02/total.00_02_11_02.Still003-1024x768.jpg)

* Installer les Additions invité VirtualBox sous Ubuntu

```bash
sudo apt update
sudo apt install build-essential dkms linux-headers-$(uname -r)
sudo sh /media/*/VBox*/VBoxLinuxAdditions.run
sudo reboot
```

* Activer l'option


![LED Matrix Wiring 1](https://enrootmauvaisetroupe.fr/wp-content/uploads/2022/02/total.00_02_11_02.Still003-1024x768.jpg)

