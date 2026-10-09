---
title: 'PWA Studio : le navigateur affiche l’erreur « Impossible de remplacer par »'
description: Cette rubrique présente une solution lorsque votre navigateur web affiche un « *Impossible d’activer le proxy de* » et que la console affiche un
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%
---
# PWA Studio : le navigateur affiche l’erreur « Impossible de remplacer par »

Cette rubrique présente une solution lorsque votre navigateur web affiche un « *Impossible d’utiliser le proxy pour* » et que la console affiche un

```
ENOTFOUND
```

Erreur lors de l’utilisation de Progressive Web App (PWA) Studio pour Adobe Commerce.

## Produits et versions concernés

* PWA Studio pour Adobe Commerce

## Problème

<u>Étape à reproduire</u> :

* Chargez votre boutique Adobe Commerce dans un navigateur.

<u>Résultat attendu </u> :

* La boutique Adobe Commerce se charge normalement dans votre navigateur.

<u>Résultat réel</u> :

* Votre navigateur web affiche l’erreur « *Impossible d’envoyer le proxy à* » et la console affiche une erreur du type :

```
    ENOTFOUND
```


## Cause

NodeJS ne peut pas résoudre le nom d’hôte de votre magasin Adobe Commerce.

## Solution

1. Assurez-vous que votre boutique Adobe Commerce se charge dans plusieurs navigateurs web.
1. Si vous exécutez un serveur DNS local ou un VPN, ajoutez une entrée à votre fichier d’hôte (situé dans `/etc/hosts`) et mappez manuellement ce domaine ([Instructions génériques sur la modification du fichier d’hôte](https://linuxize.com/post/how-to-edit-your-hosts-file/)) pour que NodeJS puisse le résoudre.

## Lecture connexe

* [Documentation de PWA Studio for Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/)
* [Outils et bibliothèques](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/)
