---
title: Appliquez un correctif pour continuer à proposer DHL comme opérateur de transport
description: Cet article fournit un correctif, permettant aux commerçants utilisant Adobe Commerce 2.4.4 et versions antérieures de continuer à proposer la livraison DHL, une fois que le schéma DHL 6.0 est obsolète de fin juillet à septembre 2022.
exl-id: 4350e83a-495b-41b4-a526-dae5923e9d41
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Appliquez un correctif pour continuer à proposer DHL comme opérateur de transport


## Produits et versions concernés

* Adobe Commerce 2.4.4 et versions antérieures, toutes les méthodes de déploiement.

## Problème

DHL introduit une version de schéma 6.2 et abandonne la version 6.0 d’ici la fin juillet à septembre 2022. L’intégration DHL d’Adobe Commerce 2.4.4 et versions antérieures ne prend en charge que la version 6.0.

## Solution

Adobe Commerce 2.4.5, dont la publication est prévue pour août 2022, contiendra l’intégration mise à niveau avec DHL utilisant le schéma de version 6.2. Tant que la nouvelle version n’est pas publiée (ou si vous choisissez de ne pas effectuer la mise à niveau), nous vous encourageons à appliquer le correctif AC-3022, mettant en oeuvre la prise en charge du schéma DHL version 6.2, afin de continuer à proposer des envois DHL dans votre boutique après l’obsolescence.

## Correctif

L’ID de correctif est AC-3022 disponible dans la version 1.1.16 de l’outil Correctifs de qualité.
Pour plus d’informations sur l’utilisation du protocole QPT et l’installation des correctifs, reportez-vous à l’article [Outil de correctifs de qualité (QPT) > Utilisation](https://devdocs.magento.com/quality-patches/usage.html) de notre documentation destinée aux développeurs.

Le correctif s’applique aux versions Adobe Commerce suivantes :

* 2.4.0 - 2.4.4-p1
* 2.3.7

## Lecture connexe

* [Carrières de livraison > DHL](https://docs.magento.com/user-guide/shipping/dhl.html) dans notre guide d’utilisation
* [Méthodes de diffusion](https://docs.magento.com/user-guide/configuration/sales/delivery-methods.html) dans notre guide d’utilisation
