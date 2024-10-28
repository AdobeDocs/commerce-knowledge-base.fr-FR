---
title: "Problème connu d’Adobe Commerce 2.3.5 : commandes multi-produits virtuelles"
description: Cet article explique un problème connu dans Adobe Commerce 2.3.5, en raison duquel une commande multi-expédition contenant un produit virtuel n’est pas traitée correctement.
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: d51fd4d7b064b8eea6cd3771af279b74a8bdec48
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Problème connu d’Adobe Commerce 2.3.5 : commandes multi-produits virtuelles

Cet article explique un problème connu dans Adobe Commerce 2.3.5, en raison duquel une commande multi-expédition contenant un produit virtuel n’est pas traitée correctement.

## Produits et versions concernés

* Adobe Commerce on-premise 2.3.5
* Adobe Commerce sur l’infrastructure cloud 2.3.5

## Problème

<u>Étapes à reproduire</u> :

1. Sur le storefront, ajoutez des produits physiques et virtuels au panier.
1. Passez à la caisse et sélectionnez **Extraire avec plusieurs adresses**.
1. Ajoutez toutes les informations requises et passez la commande.

<u>Résultat attendu</u> :

Les commandes sont passées avec succès pour tous les produits.

<u>Résultat réel</u> :

La commande du produit virtuel est vide.

## Correction

Un correctif sera disponible dans Adobe Commerce 2.3.6, dont la sortie est prévue au quatrième trimestre 2020.

## Lecture connexe

Dans notre base de connaissances de soutien :

* [Problème connu de la comparaison de produits dans Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Problème connu du comptage de produit d’action en bloc dans Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Problème lié au mode de paiement par pays dans Adobe Commerce 2.3.5 et 2.3.5-p1](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Correctif du problème de paiement Amazon dans Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

Dans notre documentation destinée aux développeurs :

* [Notes de mise à jour d’Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
