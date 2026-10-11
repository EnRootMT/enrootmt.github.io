---
title: Windows 11: Probleme d’appairage bluetooth avec manettes PS4
date: 2026-10-11
categories: [Tutoriels, Windows]
tags: [ssh, clé publique, clé privée]
---

# Windows 11 : résoudre les problèmes de connexion des manettes PS4 avec Intel AX201

Impossible de connecter une manette PS4 (DualShock 4) en Bluetooth sous Windows 11 ? La manette clignote, mais Windows ne la détecte jamais ?

J'ai rencontré exactement ce problème avec deux manettes Sony officielles et un contrôleur **Intel AX201**.

Après plusieurs tentatives infructueuses, j'ai finalement trouvé une solution : **installer une ancienne version du pilote Bluetooth Intel, la 21.0.0.4**.

## Le problème

Sur mon PC Windows 11, impossible de connecter mes deux manettes DualShock 4 en Bluetooth.

Les symptômes étaient les suivants :

- Les manettes passaient correctement en mode appairage, avec un clignotement blanc rapide.
- Windows ne détectait aucun périphérique `Wireless Controller`.
- Les autres périphériques Bluetooth fonctionnaient normalement.
- Les deux manettes étaient immédiatement détectées sur Android.
- La mise à jour vers un pilote Intel plus récent ne changeait rien.

J'ai également essayé l'ancien assistant d'appairage Windows, accessible avec :

```powershell
devicepairingwizard
```

Sans succès : aucune des deux manettes n'apparaissait.

## Identifier son chipset Bluetooth

Pour connaître le contrôleur Bluetooth utilisé, ouvrir le **Gestionnaire de périphériques** :

1. Développer la rubrique **Bluetooth**.
2. Double-cliquer sur **Intel(R) Wireless Bluetooth(R)**.
3. Ouvrir l'onglet **Détails**.
4. Sélectionner **ID de matériel**.

Dans mon cas :

```text
USB\VID_8087&PID_0026&REV_0002
```

Pour identifier le modèle de la carte Intel, on peut également utiliser PowerShell :

```powershell
Get-NetAdapter | Select-Object Name, InterfaceDescription
```

Résultat :

```text
Intel(R) Wi-Fi 6 AX201 160MHz
```

Ma configuration :

| Élément | Valeur |
|---|---|
| Système | Windows 11 |
| Contrôleur | Intel Wi-Fi 6 AX201 |
| Bluetooth | Intel Wireless Bluetooth |
| Identifiant matériel | VID_8087 / PID_0026 |
| Pilote initial | 23.90.0.8 |
| Date du pilote | 18 octobre 2024 |

## La solution : installer le pilote Intel Bluetooth 21.0.0.4

En cherchant sur les forums Intel, j'ai découvert que plusieurs utilisateurs rencontraient des problèmes avec les contrôleurs Bluetooth AX200, AX201 et AX210, notamment avec les manettes de jeu.

Certains rapportaient une amélioration en revenant à un ancien pilote Intel.

J'ai donc essayé la version **21.0.0.4, datant de 2019**, et cela a fonctionné !

### 1. Télécharger le pilote

Le pilote est disponible sur le site de Dell :

**[Intel Wireless Bluetooth 21.0.0.4 – Dell Support](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=d6k9x)**

### 2. Installer l'ancien pilote

1. Télécharger le pilote depuis le site Dell.
2. Installer la version 21.0.0.4 sur Windows.
3. Redémarrer l'ordinateur.

Le pilote étant ancien, il faut vérifier sa compatibilité avec son matériel. Cette manipulation n'est pas une recommandation générale de conserver un pilote obsolète.

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

## Conclusion

Si vous possédez un contrôleur Bluetooth Intel AX201 et que Windows 11 refuse de détecter vos manettes PS4, la version du pilote mérite d'être examinée.

Dans mon cas, ni les manipulations habituelles ni la mise à jour du pilote n'avaient permis de résoudre le problème.

**C'est finalement le retour à l'ancien pilote Intel Bluetooth 21.0.0.4 qui a permis de connecter les manettes.**

Une solution simple qui m'a évité d'acheter un adaptateur Bluetooth USB supplémentaire.

Attention néanmoins : il s'agit d'un retour d'expérience sur une configuration précise. Ce pilote de 2019 ne bénéficie pas des correctifs de sécurité récents et son utilisation doit rester un choix de dépannage éclairé.
