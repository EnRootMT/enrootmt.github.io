---
title: Comment récupérer la clé publique depuis une clé privée SSH
date: 2021-04-15
categories: [Tutoriels, Linux]
tags: [ssh, clé publique, clé privée]
---

# Comment récupérer la clé publique depuis une clé privée SSH

Je ne sais comment je me suis débrouillée mais j'ai réussit à perdre ma clé publique sur mon WSL (*Windows Subsystem for Linux*).

La clé privée, elle, est toujours là.

Du coup il a fallut que je recrée ma clé publique parce que j'avais besoin d'aller la poser sur un serveur.

Pour ça il suffit d'utiliser la commande suivante :

~~~bash
ssh-keygen -y -f ~/.ssh/id_rsa > ~/.ssh/id_rsa.pub
~~~

Et voilà, j'ai retrouvé ma clé publique !
