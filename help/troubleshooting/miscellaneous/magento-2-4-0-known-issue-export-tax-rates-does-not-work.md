---
title: Problème connu d’Adobe Commerce 2.4.0 - Les taux de taxe d’exportation ne fonctionnent pas
description: Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0 qui fait que le bouton **Exporter les taux de taxe** ne fonctionne pas.
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Problème connu d’Adobe Commerce 2.4.0 - Les taux de taxe d’exportation ne fonctionnent pas

Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0 dans lequel la variable **Exporter les taux de taxe** ne fonctionne pas.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problème

<u>Étapes à reproduire :</u>

1. Accédez au Panneau d’administration de Commerce > **Magasins** > **Règles fiscales**.
1. Cliquez sur le bouton **Ajouter une nouvelle règle fiscale** bouton .
1. Cliquez sur le texte de la variable **Exporter les taux de taxe** bouton .

   ![magento_export_tax_rates.png](assets/mceclip0.png)

<u>Résultat attendu</u>:

A `tax_rates.csv` téléchargements de fichiers contenant des taux d’imposition.

<u>Résultat réel</u>:

Aucun fichier .csv n’est téléchargé.

## Solution

Solution :

Cliquez sur le bord inférieur gauche de la **Exporter les taux de taxe** pour exporter le `tax_rates.csv` fichier .

![magento_export_tax_rates.png](assets/mceclip1.png)

Il est prévu que le problème soit résolu dans un correctif 2.4.1.

## Lecture connexe

Dans notre base de connaissances de soutien :

* [Problème connu d’Adobe Commerce 2.4.0 : les méthodes de paiement du Braintree ne s’affichent pas dans le passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md).
* [Problème connu de création des libellés d’expédition dans Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md).
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md).
* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur le storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md).
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton &quot;Ajouter des sélections à mon panier&quot; ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md).
