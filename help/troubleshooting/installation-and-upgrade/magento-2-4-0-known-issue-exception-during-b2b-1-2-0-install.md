---
title: "Adobe Commerce 2.4.0 : exception lors de l’installation B2B 1.2.0"
description: Cet article fournit un correctif pour un problème connu d’Adobe Commerce pour une exception générée lors de "setup:upgrade" lors de l’installation de B2B 1.2.0.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 : exception lors de l’installation B2B 1.2.0

Cet article fournit un correctif pour un problème connu d’Adobe Commerce pour une exception générée pendant la `setup:upgrade` lors de l’installation de B2B 1.2.0.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0
* B2B 1.2.0

## Problème

<u>Étapes à reproduire</u>

1. Installez Adobe Commerce avec plusieurs magasins créés.
1. Créez un magasin supplémentaire.
1. Installez B2B 1.2.0.

>[!WARNING]
>
>La mise à niveau de toute instance B2B comportant plus d’un magasin à partir d’une version inférieure à 1.2.0 ou d’une instance Commerce inférieure à 2.4.0 est également affectée.

<u>Résultat attendu</u>

B2B 1.2.0 installe .

<u>Résultat réel</u>

When `setup:upgrade` s’exécute pour installer B2B 1.2.0. Cette erreur s’affiche sur la page `PurchaseOrder` module :

```php
Module 'Magento_PurchaseOrder':
  Unable to apply data patch Magento\PurchaseOrder\Setup\Patch\Data\InitPurchaseOrderSalesSequence
  for module Magento_PurchaseOrder. Original exception message: DDL statements
  are not allowed in transactions
```

## Solution

Appliquez le correctif fourni dans cet article.

## Correctif

Le correctif est joint à cet article, disponible en téléchargement dans les deux `.composer` et `.git` formats (après avoir décompressé les fichiers).

Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur l’un des liens suivants :

* [Correctif du compositeur B2B-716\_compositeur.patch](assets/B2B-716_composer.patch.zip)
* [Correctif Git B2B-716\_git.patch](assets/B2B-716_git.patch.zip)

## Comment appliquer un correctif

<u>Compositeur </u>

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour les instructions de correctif du compositeur.

<u>Correctif Git </u>

* Voir [Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans la documentation destinée aux développeurs pour les instructions de correctif git pour Adobe Commerce sur l’infrastructure cloud.
* Voir [Application de correctifs : correctifs personnalisés](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#custom-patches) dans la documentation destinée aux développeurs pour obtenir des instructions sur les correctifs git pour Adobe Commerce.

## Lecture connexe

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
