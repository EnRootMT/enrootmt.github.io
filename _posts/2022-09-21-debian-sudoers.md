---
title: Ajouter un utilisateur aux sudoers sous Debian
date: 2022-09-21
categories: [Tutoriels, Linux]
tags: [linux, sudoers]
---

## Ajouter un utilisateur aux sudoers

- Passer en root :
~~~bash
su - root
~~~

- Indiquer le mot de passe root

- Passer l'utilisateur en sudoer :
~~~bash
usermod -aG sudo enroot
~~~

- Repasser en utilisateur :
~~~bash
su - enroot
~~~

Et voilà, l'utilisateur fait maintenant partie des **sudoers**.
