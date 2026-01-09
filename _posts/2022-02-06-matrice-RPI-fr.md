---
title: Matrice de led sur Raspberry Pi
date: 2022-02-06
categories: [Tutoriels, Raspberry Pi]
tags: [raspberry pi, led, matrix, max7219]
---

# Matrice de led sur Raspberry Pi

## Introduction

Dans cet article, je vais vous expliquer comment brancher une matrice de LED montée sur un circuit MAX7219 sur un Raspberry pi.

Pour ça vous aurez besoin d'un Raspberry pi avec un Linux installé dessus (Raspberry pi os de préférence)

https://www.youtube.com/watch?v=lN-eLo0duho

---

## Branchement

Voici les numéro des pins du Raspberry.

![GPIO Pinout](https://enrootmauvaisetroupe.fr/wp-content/uploads/2022/02/GPIO-Pinout-Diagram-2-1024x588.png)

![Pins Raspberry Pi](https://enrootmauvaisetroupe.fr/wp-content/uploads/2022/02/pin.png)

Il faudra brancher la matrice de led au Raspberry en suivant les infos du tableau.

VCC sur la pin 2 du pi, GND sur la 6, ...

![Branchement LED Matrix](https://enrootmauvaisetroupe.fr/wp-content/uploads/2022/02/total.00_02_11_02.Still003-1024x768.jpg)

![Branchement LED Matrix](https://enrootmauvaisetroupe.fr/wp-content/uploads/2022/02/total.00_02_36_23.Still001-1024x768.png)

---

## Installation des librairies et modules

Dans un terminal taper les commandes suivantes:

~~~bash
sudo usermod -a -G spi,gpio pi
sudo apt-get update
sudo apt-get install build-essential python3-dev python3-pip libfreetype6-dev libjpeg-dev
sudo -i pip install --upgrade pip setuptools
sudo -H pip install --upgrade luma.led_matrix
~~~

---

## Le script

Aller sur https://github.com/rm-hull/luma.led_matrix et récupérer  
**matrix_demo.py** qui se trouve dans `examples`.

https://github.com/rm-hull/luma.led_matrix/blob/master/examples/matrix_demo.py

Dans un terminal aller dans le répertoire du script et l’exécuter avec :

~~~bash
python matrix_demo.py
~~~

Et voilà vous devriez avoir la démo qui s'affiche sur la matrice.

Maintenant vous pouvez vous amusez avec le code pour garder ce qui vous intéresse et personnaliser l'affichage.
