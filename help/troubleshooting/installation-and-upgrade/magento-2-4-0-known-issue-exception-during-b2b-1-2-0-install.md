---
title: 'Adobe Commerce 2.4.0 : exception lors de l’installation de B2B 1.2.0'
description: Cet article fournit un correctif pour un problème connu d’Adobe Commerce lié à une exception générée lors de « setup:upgrade » lors de l’installation de B2B 1.2.0.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '334'
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

</u> de correctif du compositeur<u>

Pour obtenir des instructions sur l’application d’un correctif compositeur[&#128279;](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) voir Application d’un correctif compositeur fourni par Adobe .

</u> du correctif <u>Git)

* Voir [&#x200B; Application de correctifs &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans la documentation destinée aux développeurs pour obtenir des instructions sur les correctifs Git pour Adobe Commerce sur les infrastructures cloud.
* Voir [&#x200B; Application de correctifs : correctifs personnalisés &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches) dans la documentation destinée aux développeurs pour obtenir des instructions sur les correctifs Git pour Adobe Commerce.

## Lecture connexe

* [Problème connu dans Adobe Commerce 2.4.0 : les méthodes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu dans Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
