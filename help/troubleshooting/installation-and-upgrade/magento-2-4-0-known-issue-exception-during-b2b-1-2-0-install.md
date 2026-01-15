---
title: 'Adobe Commerce 2.4.0 : exception lors de l’installation de B2B 1.2.0'
description: Cet article fournit un correctif pour un problème connu d’Adobe Commerce lié à une exception générée lors de « setup:upgrade » lors de l’installation de B2B 1.2.0.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 : exception lors de l’installation de B2B 1.2.0

Cet article fournit un correctif pour un problème connu d’Adobe Commerce lié à une exception générée lors de l’`setup:upgrade` lors de l’installation de B2B 1.2.0.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0
* B2B 1.2.0

## Problème

<u>Procédure à suivre</u>

1. Installez Adobe Commerce avec plusieurs magasins créés.
1. Créez un magasin supplémentaire.
1. Installer B2B 1.2.0.

>[!WARNING]
>
>La mise à niveau de toute instance B2B avec plus d’un magasin à partir d’une version inférieure à 1.2.0 ou d’une instance Commerce inférieure à 2.4.0 est également affectée.

<u>Résultat attendu</u>

Installation de B2B 1.2.0.

<u>Résultat réel</u>

Lorsque `setup:upgrade` s’exécute pour installer B2B 1.2.0, cette erreur s’affiche sur le module `PurchaseOrder` :

```php
Module 'Magento_PurchaseOrder':
  Unable to apply data patch Magento\PurchaseOrder\Setup\Patch\Data\InitPurchaseOrderSalesSequence
  for module Magento_PurchaseOrder. Original exception message: DDL statements
  are not allowed in transactions
```

## Solution

Appliquez le correctif fourni dans cet article.

## Patch

Le correctif est joint à cet article. Il peut être téléchargé aux formats `.composer` et `.git` (après la décompression des fichiers).

Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur l’un des liens suivants :

* [Correctif du compositeur B2B-716\_composer.patch](assets/B2B-716_composer.patch.zip)
* [Correctif Git B2B-716\_git.patch](assets/B2B-716_git.patch.zip)

## Application d’un correctif

<u></u> de correctif du compositeur

Pour obtenir des instructions sur l’application d’un correctif compositeur[ voir ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)Application d’un correctif compositeur fourni par Adobe .

<u> du correctif </u>Git)

* Voir [ Application de correctifs ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans la documentation destinée aux développeurs pour obtenir des instructions sur les correctifs Git pour Adobe Commerce sur les infrastructures cloud.
* Voir [ Application de correctifs : correctifs personnalisés ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches) dans la documentation destinée aux développeurs pour obtenir des instructions sur les correctifs Git pour Adobe Commerce.

## Lecture connexe

* [Problème connu dans Adobe Commerce 2.4.0 : les méthodes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu dans Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [L’administrateur B2B d’Adobe Commerce 2.4.0 ne peut pas ajouter de produit configurable au devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
