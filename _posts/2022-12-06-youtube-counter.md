---
title: Build a YouTube Subscriber Counter
date: 2022-12-06
categories: [Tutoriels]
tags: [youtube, subscriber counter, led matrix, raspberry pi, python]
---

# Build a YouTube Subscriber Counter

In this article you will find additional information related to the following video:

👉 https://youtu.be/rznTcP93Rmo

## Google API

### Google API Console
https://console.developers.google.com

### Test request
~~~text
https://www.googleapis.com/youtube/v3/channels?part=statistics&id="CHANNEL_ID"&key="API_KEY"
~~~

### Scripts

#### Python: Display subscribers
https://github.com/EnRootMT/compteurYT/blob/main/compteur.py

#### Install Google API Python module
~~~bash
python -m pip install --upgrade google-api-python-client
~~~

#### Display subscribers on the LED matrix
https://github.com/EnRootMT/compteurYT/blob/main/abos.py

## LED Matrix connection to the Raspberry Pi

https://enrootmauvaisetroupe.fr/index.php/2022/11/29/how-to-use-an-led-matrix-with-a-raspberry-pi/

## Libraries and modules installation

In a terminal, type:

~~~bash
sudo usermod -a -G spi,gpio pi
sudo apt-get update
sudo apt-get install build-essential python3-dev python3-pip libfreetype6-dev libjpeg-dev
sudo -i pip install --upgrade pip setuptools
sudo -H pip install --upgrade luma.led_matrix
~~~

## Additional Scripts

### Weather
https://github.com/EnRootMT/compteurYT/blob/main/meteo.py

### Subscribers and weather
https://github.com/EnRootMT/compteurYT/blob/main/abos_meteo.py

## Sources and documentation

https://www.youtube.com/watch?v=T0DmHRdtqY0
