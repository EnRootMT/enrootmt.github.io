---
title: Ubuntu double boot – Mettre Windows en premier en CLI
date: 2020-10-07
categories: [Tutoriels, Linux]
tags: [ubuntu, windows, grub, dual boot, cli]
---

# Ubuntu double boot – Mettre Windows en premier en CLI

Vous avez installé Ubuntu en double boot avec Windows sur votre PC et vous souhaitez que Windows démarre par défaut.

Dans cet article, je vous explique comment paramétrer **grub en ligne de commande** pour y parvenir.

---

## Récupérer le nom

On commence par récupérer le nom de la "ligne Windows" en cherchant dans le fichier *** les lignes qui contiennent `menuentry`.

~~~bash
sudo grep menuentry /boot/grub/grub.cfg
~~~

Vous devriez avoir un résultat dans ce style là :

~~~text
enroot@machinelinux:~$ sudo grep menuentry /boot/grub/grub.cfg
if [ x"${feature_menuentry_id}" = xy ]; then
menuentry_id_option="--unrestricted --id"
menuentry_id_option="--unrestricted"
export menuentry_id_option
menuentry 'Ubuntu, avec Linux 4.15.0-118-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-118-generic-advanced-d57303e4-267b-4938-a17e-01fc6d61772e' {
menuentry 'Windows Boot Manager (sur /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-efi-3857-151F' {
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
~~~

Copier l'entrée Windows, ici :

~~~text
'Windows Boot Manager (sur /dev/sda1)'
~~~

---

## Modifier grub

Éditer le fichier grub :

~~~bash
sudo nano /etc/default/grub
~~~

ou

~~~bash
sudo gedit /etc/default/grub
~~~

si vous préférez le mode graphique.

Modifier `GRUB_DEFAULT=` en indiquant le système par défaut :

~~~text
GRUB_DEFAULT='Windows Boot Manager (sur /dev/sda1)'
~~~

Sauvegarder et quitter.

---

## Mettre à jour Grub

On fini par une mise à jour de grub avec :

~~~bash
update-grub
~~~

Et voilà, vous devriez maintenant booter sur **Windows par défaut** !
