---
title: L’abandon de l’expédition prend une mauvaise adresse
description: La solution d’expédition ne récupère pas l’adresse de la source du produit.
exl-id: ce89713f-d506-4e4f-bf49-cdee3e6d29b5
feature: Customer Service, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# L’abandon de l’expédition prend une mauvaise adresse

## Problème

La solution d’expédition ne récupère pas l’adresse de la source du produit.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud (toutes les versions), avec le stock de Magento installé
* Adobe Commerce On-Premise 2.3.0 et versions ultérieures, avec l’installation de Magento Inventory
* Magento Open Source 2.3.0 et versions ultérieures, avec l’inventaire du Magento installé

### Cause

L’inventaire des Magento ne prend actuellement pas en charge l’utilisation du calcul des taux d’expédition par défaut en fonction de l’adresse source lors du passage en caisse. L’adresse de magasin par défaut de la configuration est utilisée dans tous les cas.

## Lecture connexe

* [FAQ sur l’inventaire des Magento](https://github.com/magento/inventory/wiki/MSI-FAQs) dans GitHub.
