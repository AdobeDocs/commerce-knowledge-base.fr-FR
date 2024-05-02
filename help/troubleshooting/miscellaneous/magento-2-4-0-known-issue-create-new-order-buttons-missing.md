---
title: "Problème connu d’Adobe Commerce 2.4.0 : absence des boutons Créer une commande"
description: Cet article fournit une solution à un problème connu dans l’administration de Commerce pour deux boutons manquants sur la page de création de commande. Lors de la création d’une commande pour un nouveau client ou un client existant, il n’est pas possible d’ajouter des produits à la commande à partir du catalogue, car les boutons **Ajouter des produits par SKU** et **Ajouter des produits** sont manquants. Cela est dû à l’activation du regroupement JS. Un correctif sera disponible dans Adobe Commerce 2.4.1.
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Problème connu d’Adobe Commerce 2.4.0 : absence des boutons Créer un ordre

Cet article fournit une solution à un problème connu dans l’administration de Commerce pour deux boutons manquants sur la page de création de commande. Lors de la création d’une commande pour un nouveau client ou un client existant, il n’est pas possible d’ajouter des produits à la commande à partir du catalogue depuis la variable **Ajout de produits par SKU** et **Ajouter des produits** les boutons sont manquants. Cela est dû à l’activation du regroupement JS. Un correctif sera disponible dans Adobe Commerce 2.4.1.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

<u>Étapes à reproduire</u>

1. Accédez à **Clients > Tous les clients**.
1. Cliquez sur le bouton **Modifier** lien sur un client.
1. Cliquez sur le bouton **Créer une commande** bouton .

<u>Résultat attendu</u>

La variable **Ajout de produits par SKU** et **Ajouter des produits** des boutons **Créer une commande** page.

<u>Résultat réel</u>

La variable **Ajout de produits par SKU** et **Ajouter des produits** n’apparaît pas sur les boutons **Créer une commande** page.

## Solution

La solution à ce problème consiste à désactiver le regroupement JS pour l’instance Adobe Commerce. Le problème devrait être résolu dans Adobe Commerce 2.4.1, dont la sortie est prévue au 4e trimestre 2020.

## Lectures connexes dans notre base de connaissances de support

* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur le storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les méthodes de paiement du Braintree ne s’affichent pas dans le passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur 404 lors de la suppression des points de récompense lors du passage en caisse multi-expédition](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur d’affichage des commandes](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [L’administrateur d’Adobe Commerce 2.4.0 B2B ne peut pas ajouter de produit configurable pour le devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problème connu de création des libellés d’expédition dans Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton &quot;Ajouter des sélections à mon panier&quot; ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
