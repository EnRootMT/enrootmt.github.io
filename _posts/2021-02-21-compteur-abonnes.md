---
title: Fabriquer un compteur d'abonnés YouTube
date: 2021-02-21
categories: [Tutoriels]
tags: [youtube api, compteur abonnés, led matrix, raspberry pi, python]
---

# Fabriquer un compteur d'abonnés YouTube

Dans cet article vous trouverez les informations complémentaires à la vidéo suivante :

https://youtu.be/fb0zcw6IO40

---

## API google

### Site api google
https://console.developers.google.com

### Test
https://www.googleapis.com/youtube/v3/channels?part=statistics&id="ID_CHAINE"&key="CLE_API"

### Scripts

#### Affichage abonnements Python
https://github.com/EnRootMT/compteurYT/blob/main/compteur.py

#### Installation module api google
~~~bash
python -m pip install --upgrade google-api-python-client
~~~

#### Affichage abonnements matrice de led
https://github.com/EnRootMT/compteurYT/blob/main/abos.py

---

## Branchement de la matrice au Raspberry Pi
https://enrootmauvaisetroupe.fr/index.php/2022/02/06/matrice-de-led-sur-raspberry-pi/

---

## Installation des librairies et modules

Dans un terminal taper les commandes suivantes :

~~~bash
sudo usermod -a -G spi,gpio pi
sudo apt-get update
sudo apt-get install build-essential python3-dev python3-pip libfreetype6-dev libjpeg-dev
sudo -i pip install --upgrade pip setuptools
sudo -H pip install --upgrade luma.led_matrix
~~~

---

## Scripts

### Météo
https://github.com/EnRootMT/compteurYT/blob/main/meteo.py

### Abonnement et météo
https://github.com/EnRootMT/compteurYT/blob/main/abos_meteo.py

---

## Sources et documentation

https://www.youtube.com/watch?v=T0DmHRdtqY0
