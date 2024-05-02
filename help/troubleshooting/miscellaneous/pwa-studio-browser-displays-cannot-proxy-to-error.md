---
title: '"PWA Studio : le navigateur affiche "Impossible de remplacer par "erreur"'
description: Cette rubrique traite d’une solution lorsque votre navigateur web affiche un "*Ne peut pas remplacer par*" et que la console affiche une
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# PWA Studio : le navigateur affiche l’erreur &quot;Impossible de remplacer par&quot;

Cette rubrique traite d’une solution lorsque votre navigateur web affiche le message &quot;*Ne peut pas remplacer par*&quot; et la console affiche une

```
ENOTFOUND
```

lors de l’utilisation de Progressive Web App (PWA) Studio pour Adobe Commerce.

## Produits et versions concernés

* PWA Studio pour Adobe Commerce

## Problème

<u>Étape à reproduire</u>:

* Chargez votre boutique Adobe Commerce dans un navigateur.

<u>Résultat attendu</u>:

* La boutique Adobe Commerce se charge normalement dans votre navigateur.

<u>Résultat réel</u>:

* Votre navigateur Web affiche le *Ne peut pas remplacer par*&quot;erreur et la console affiche une erreur du type :

```
    ENOTFOUND
```


## Cause

NodeJS ne peut pas résoudre le nom d’hôte de votre boutique Adobe Commerce.

## Solution

1. Assurez-vous que votre boutique Adobe Commerce est chargée dans plusieurs navigateurs web.
1. Si vous exécutez un serveur DNS local ou un VPN, ajoutez une entrée à votre fichier d’hôtes (situé dans `/etc/hosts`) et mapper manuellement ce domaine ([Instructions génériques sur la modification des fichiers hôtes](https://linuxize.com/post/how-to-edit-your-hosts-file/)) afin que NodeJS puisse le résoudre.

## Lecture connexe

* [PWA Studio pour la documentation Adobe Commerce](https://magento.github.io/pwa-studio/)
* [Outils et bibliothèques](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
