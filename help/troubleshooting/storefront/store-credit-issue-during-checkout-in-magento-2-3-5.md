---
title: Problème de crédit de magasin lors du passage en caisse dans Adobe Commerce 2.3.5
description: Cet article fournit une solution au problème connu lié au crédit de magasin lors du passage en caisse dans Adobe Commerce 2.3.5, où les clients rencontrent des erreurs lors du passage en caisse après avoir sélectionné puis supprimé l’utilisation du crédit de magasin. Un correctif permanent sera disponible dans Adobe Commerce 2.3.6.
exl-id: a0cca226-4d95-40b3-bd37-f13d28591366
feature: Checkout, Orders, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Problème de crédit de magasin lors du passage en caisse dans Adobe Commerce 2.3.5

Cet article fournit une solution au problème connu lié au crédit de magasin lors du passage en caisse dans Adobe Commerce 2.3.5, où les clients rencontrent des erreurs lors du passage en caisse après avoir sélectionné puis supprimé l’utilisation du crédit de magasin. Un correctif permanent sera disponible dans Adobe Commerce 2.3.6.

## Produits et versions concernés

* Adobe Commerce on-premise 2.3.5
* Adobe Commerce sur l’infrastructure cloud 2.3.5

## Problème

<u>Étapes à reproduire</u>:

1. Le client ajoute des produits au panier et procède au passage en caisse.
1. Le client spécifie le crédit de magasin comme mode de paiement.
1. Le client supprime le crédit de la boutique et modifie le mode de paiement.
1. Le client passe en caisse.

<u>Résultats attendus</u>:

Toutes les informations de commande s’affichent correctement.

<u>Résultats réels</u>:

Adobe Commerce renvoie une erreur dans la section Résumé de la commande de la page Commande.

## Solution

Les clients peuvent actualiser la page Commande et les informations dans le Résumé de la commande se chargeront correctement. Un correctif sera disponible dans Adobe Commerce 2.3.6, dont la sortie est prévue au quatrième trimestre 2020.

## Lecture connexe

Articles relatifs aux problèmes connus d’Adobe Commerce 2.3.5 dans notre base de connaissances de support :

* [Commandes multi-expédition avec un produit virtuel non traité correctement dans Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)

* [Problème lié au mode de paiement par pays dans Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.5 et 2.3.5-p1](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)

* [Adobe Commerce invite les clients à se connecter, mais fournit un lien non valide](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)

* [Problème connu du comptage de produit d’action en bloc dans Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)

* [Correctif du problème de paiement Amazon dans Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

* [Problème de comparaison des produits dans Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)

Dans notre documentation destinée aux développeurs :

* [Problèmes connus d’Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
