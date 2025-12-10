---
title: 'problème connu d’Adobe Commerce 2.3.5 : commandes de produits virtuels avec expédition multiple'
description: Cet article explique un problème connu dans Adobe Commerce 2.3.5, où une commande à expédition multiple contenant un produit virtuel n’est pas traitée correctement.
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: 39e61a3fe8b75fb613819d89c7d47acdf1c384f6
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# problème connu d’Adobe Commerce 2.3.5 : commandes de produits virtuels avec expédition multiple

Cet article explique un problème connu dans Adobe Commerce 2.3.5, où une commande à expédition multiple contenant un produit virtuel n’est pas traitée correctement.

## Produits et versions concernés

* Adobe Commerce on-premise 2.3.5
* Adobe Commerce sur l’infrastructure cloud 2.3.5

## Problème

<u>Procédure à suivre </u> :

1. Sur le storefront, ajoutez des produits physiques et virtuels au panier.
1. Passez à l’extraction et sélectionnez **Extraire avec plusieurs adresses**.
1. Ajoutez toutes les informations requises et passez la commande.

<u>Résultat attendu </u> :

Les commandes sont passées pour tous les produits avec succès.

<u>Résultat réel</u> :

La commande du produit virtuel est vide.

## Correctif

Un correctif sera disponible dans Adobe Commerce 2.3.6, dont la publication est prévue pour le 4e trimestre 2020.

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [Notes De Mise À Jour D’Adobe Commerce 2.3.5](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
