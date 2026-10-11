---
title: "Windows 11: Probleme d’appairage bluetooth avec manettes PS4"
date: 2026-10-11
categories: [Tutoriels, Windows]
tags: [Windows 11, Bluetooth, Intel AX201, DualShock 4, PS4, pilotes, drivers]
---

# Windows 11 : résoudre les problèmes de connexion des manettes PS4 avec Intel AX201

Impossible de connecter une manette PS4 (DualShock 4) en Bluetooth sous Windows 11 ? La manette est en mode appairage, elle clignote, mais Windows ne la détecte pas ?

J'ai rencontré ce problème avec mes deux manettes Sony officielles.

Ma carte mère est un Z690-plus wifi D4 équipée d'un contrôleur wifi et Bluetooth **Intel AX201**.

Après plusieurs tentatives infructueuses, j'ai finalement trouvé une solution : **installer une ancienne version du pilote Bluetooth **.

## Identifier son chipset Bluetooth et ses pilotes

### En graphique

Pour connaître le contrôleur Bluetooth utilisé, ouvrir le **Gestionnaire de périphériques** :

1. Développer la rubrique **Bluetooth**.
2. Double-cliquer sur **Intel(R) Wireless Bluetooth(R)**. (si vous avez du intel)
3. Ouvrir l'onglet **Détails**.
4. Sélectionner **Numéro d'identification du matériel**.

Dans mon cas :

```text
USB\VID_8087&PID_0026&REV_0002
```
5. Ouvrir l'onglet **Pilote** pour avoir la version de votre driver

### Avec powershell

Pour identifier le modèle de la carte Intel, on peut également utiliser PowerShell :

```powershell
Get-NetAdapter | Select-Object Name, InterfaceDescription
```

Résultat :

```text
Intel(R) Wi-Fi 6 AX201 160MHz
```
![activate](/assets/img/manette_ps4/Screenshot-2026-10-11-085032.png)

### Ma configuration :

| Élément | Valeur |
|---|---|
| Système | Windows 11 |
| Contrôleur | Intel Wi-Fi 6 AX201 |
| Bluetooth | Intel Wireless Bluetooth |
| Identifiant matériel | VID_8087 / PID_0026 |
| Pilote initial | 23.90.0.8 |
| Date du pilote | 18 octobre 2024 |

## La solution : installer le pilote Intel Bluetooth 21.0.0.4

En cherchant sur reddit et des forums, j'ai découvert que plusieurs utilisateurs rencontraient des problèmes avec les contrôleurs Bluetooth AX200, AX201 et AX210, notamment avec les manettes de jeu.

Certains rapportaient une amélioration en revenant à un ancien pilote Intel.

J'ai donc essayé la version **21.0.0.4, datant de 2019**, et cela a fonctionné !

### 1. Télécharger le pilote

Le pilote est disponible sur le site de Dell :

**[Intel Wireless Bluetooth 21.0.0.4 – Dell Support](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=d6k9x)**

Ou sur mon google drive:

**[Intel Wireless Bluetooth 21.0.0.4 – Google Drive](https://drive.google.com/file/d/1z3AyrIJZiA3dIZJO_IAueZEXictfumnN/view?usp=sharing)**


### 2. Installer l'ancien pilote

![activate](/assets/img/manette_ps4/2026-10-11-092923.png)

Si j'essaie d'installer directement le driver, je me retrouve avec un message d'erreur.

![activate](/assets/img/manette_ps4/2026-10-11-092648.png)

Pour contourner le problème il faut choisir **extract**.
Notez bien où vous avez extrait les fichiers.
Allez dans **drivers\Drivers\Production\Windows10-x64** et lancez **dpinst.exe** 
3. Redémarrer l'ordinateur.

Et voilà, ça devrait marcher maintenant!

### 3. Connecter les manettes PS4

Une fois le pilote installé :

1. Activer le Bluetooth sous Windows 11.
2. Maintenir simultanément **SHARE + PS** sur la manette pendant environ 5 secondes.
3. Attendre que la barre lumineuse clignote rapidement en blanc.
4. Lancer la recherche de périphériques Bluetooth.
5. Sélectionner **Wireless Controller**.

Et cette fois, Windows détecte la manette !

## Résultat

**Le remplacement du pilote Intel 23.90.0.8 par la version 21.0.0.4 a résolu mon problème.**

Mes deux manettes DualShock 4 officielles, auparavant totalement invisibles sous Windows 11, sont désormais détectées en Bluetooth.

Le problème ne venait donc ni des manettes ni de leur mode appairage, mais était lié au pilote Bluetooth utilisé sur cette configuration.

Par contre j'ai réinstaller par la suite un pilote plus récent et ça a continué de fonctionner.
Les mystères de l'informatique ...
