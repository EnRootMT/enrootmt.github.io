---
title: XRDP – Changer l'environnement de bureau par défaut
date: 2022-03-16
categories: [Tutoriels, Linux]
tags: [xrdp, ubuntu, rdp, desktop, linux]
---

## XRDP – Changer l'environnement de bureau par défaut

Si vous vous connectez en **RDP** à une machine **Ubuntu** avec **XRDP** et que vous ne voulez pas vous farcir **Gnome**, voici une commande bien pratique pour changer l'environnement de bureau par défaut.

~~~bash
sudo update-alternatives --config x-session-manager
~~~

Ensuite, il suffit de choisir l'environnement souhaité  
⚠️ *(il faut bien entendu l'avoir installé au préalable)*

![Choix de l'environnement de bureau](https://enrootmauvaisetroupe.fr/wp-content/uploads/2022/03/desktopenv-1024x291.png)

Et voilà 🎉  
Vous pouvez maintenant vous connecter en **RDP** et retrouver votre environnement de bureau préféré.
