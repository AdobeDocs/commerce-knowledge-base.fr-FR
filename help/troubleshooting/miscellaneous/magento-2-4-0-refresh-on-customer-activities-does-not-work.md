---
title: "Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas"
description: Cet article fournit une solution au problème connu d’Adobe Commerce 2.4.0 lorsqu’un utilisateur administrateur crée une commande pour un client et que les boutons d’actualisation du panneau latéral Activités du client ne fonctionnent pas.
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas

Cet article fournit une solution au problème connu d’Adobe Commerce 2.4.0 lorsqu’un utilisateur administrateur crée une commande pour un client et que les boutons d’actualisation du panneau latéral Activités du client ne fonctionnent pas.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

<u>Étapes à reproduire</u> :

1. Accédez au **panneau d’administration** > **Ventes** > **Commandes**.
1. Cliquez sur le bouton **Créer une commande** .
1. Sélectionnez le client créé.
1. Positionnez-vous sur le storefront en tant que client créé.
1. Accédez à la page **Product** (Produit). Cliquez sur le bouton **Actualiser** dans la section **Produits récemment consultés** des **Activités du client**.
1. Retournez à la vitrine.
1. passé une commande à l’aide des produits créés ;
1. Revenez au **panneau d’administration** et cliquez sur le bouton **Actualiser** de la section **Derniers éléments commandés** des **activités du client**.
1. Retournez à la vitrine. Ajoutez le produit créé à la **Liste de comparaison**.
1. Revenez au **panneau d’administration**. Cliquez sur le bouton **Actualiser** de la section **Produits dans la liste de comparaison** des **Activités du client**.
1. Retournez à la vitrine.
1. Supprimez le produit créé de la **liste de comparaison**.
1. Revenez au **panneau d’administration**.
1. Cliquez sur le bouton **Actualiser** de la section **Produits récemment comparés** des **Activités du client**.
1. Retournez à la vitrine.

<u>Résultats attendus</u> :

Le nom du produit doit apparaître dans les sections **Produits récemment consultés**, **Derniers articles commandés**, **Produits dans la liste de comparaison** et **Produits récemment comparés**.

<u>Résultats réels</u> :

La page est défilée chaque fois qu’un utilisateur clique sur un bouton **Actualiser** . Le nom du produit n’apparaît pas dans la section appropriée.

## Solution

Pour pallier ce problème, l’utilisateur administrateur peut mettre à jour **les activités du client** en cliquant sur le bouton **Mettre à jour les modifications** au bas de la barre latérale. Le problème doit être résolu dans le correctif Adobe Commerce 2.4.1.

![mceclip0.png](assets/mceclip0.png)

## Lecture connexe

* [Problème connu d’Adobe Commerce 2.4.0 : les méthodes de paiement du Braintree ne s’affichent pas dans le passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur le storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton &quot;Ajouter des sélections à mon panier&quot; ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
