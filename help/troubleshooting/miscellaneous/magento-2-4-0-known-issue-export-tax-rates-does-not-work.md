---
title: Problème connu d’Adobe Commerce 2.4.0 - Les taux de taxe à l’exportation ne fonctionnent pas
description: Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0 en raison duquel le bouton **Taux de taxe à l’exportation** ne fonctionne pas.
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Problème connu d’Adobe Commerce 2.4.0 - Les taux de taxe à l’exportation ne fonctionnent pas

Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0 en raison duquel le bouton **Taux de taxe à l’exportation** ne fonctionne pas.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problème

<u>Procédure à suivre :</u>

1. Accédez au Panneau d’administration Commerce > **Magasins** > **Règles fiscales**.
1. Cliquez sur le bouton **Ajouter une nouvelle règle fiscale**.
1. Cliquez sur le texte du bouton **Exporter les taux de taxe**.

   ![magento_export_tax_rates.png](assets/mceclip0.png)

<u>Résultat attendu </u> :

Téléchargements de fichiers `tax_rates.csv` contenant les taux de taxe.

<u>Résultat réel</u> :

Aucun fichier .csv n’est téléchargé.

## Solution

Solution :

Cliquez sur le bord inférieur gauche du bouton **Exporter les taux de taxe** pour exporter le fichier `tax_rates.csv`.

![magento_export_tax_rates.png](assets/mceclip1.png)

Il est prévu que le problème soit résolu avec un correctif 2.4.1.

## Lecture connexe

Dans notre base de connaissances du support :

* [Problème connu d’Adobe Commerce 2.4.0 : les modes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md).
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md).
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton « Ajouter des sélections à mon panier » ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md).
