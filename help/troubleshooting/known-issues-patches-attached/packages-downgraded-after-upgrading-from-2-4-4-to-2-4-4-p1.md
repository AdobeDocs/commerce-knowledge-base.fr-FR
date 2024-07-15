---
title: Packages rétrogradation après mise à niveau de 2.4.4 à 2.4.4-p1
description: Cet article fournit un correctif pour le problème lorsque les commerçants de la version 2.4.4 exécutent la commande "mise à jour du compositeur", puis que les packages (modules) répertoriés ci-dessous sont rétrogradés vers leurs versions antérieures qui ne sont pas compatibles avec la version 2.4.4 et qui sont censés être utilisés uniquement avec la version 2.4.5 et ultérieures.
exl-id: 4ebdbcd7-6905-4647-b071-1e4413455f38
feature: Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Packages rétrogradation après mise à niveau de 2.4.4 à 2.4.4-p1

Cet article fournit un correctif pour le problème lorsque les commerçants de la version 2.4.4 exécutent la commande `composer update`, puis que les packages (modules) répertoriés ci-dessous sont mis à niveau vers leurs versions antérieures qui ne sont pas compatibles avec la version 2.4.4 et qui sont censés être utilisés uniquement avec la version 2.4.5 et ultérieures.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.4
* Adobe Commerce sur site 2.4.4
* Magento Open Source 2.4.4

## Problème

Il existe deux scénarios : comment ce problème peut-il se produire et comment il peut être reproduit ?

### Scénario 1

<u>Étapes à reproduire</u> :

Lors de la mise à niveau de la version 2.4.4 vers 2.4.4-p1, plusieurs modules (modules) sont mis à niveau avec une sortie similaire :

```text
Downgrading magento/module-adobe-ims (2.1.4 => 2.1.3)
Downgrading magento/module-adobe-ims-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-admin-ui (1.3.2 => 1.3.1)
Downgrading magento/module-adobe-stock-client-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-image (1.3.3 => 1.3.2)
Downgrading magento/module-adobe-stock-image-admin-ui (1.3.3 => 1.3.2)
Downgrading magento/module-banner-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-inventory (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-advanced-checkout (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-api (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-bundle-product (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-catalog-api (1.3.3 => 1.3.2)
Downgrading magento/module-inventory-configurable-product-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-configurable-product-frontend-ui (1.0.3 => 1.0.2)
Downgrading magento/module-inventory-import-export (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-in-store-pickup-admin-ui (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-frontend (1.1.3 => 1.1.2)
Downgrading magento/module-inventory-in-store-pickup-graph-ql (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-sales-admin-ui (1.1.3 => 1.1.2-p1)
Downgrading magento/module-inventory-in-store-pickup-shipping (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-low-quantity-notification (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-low-quantity-notification-api (1.2.2 => 1.2.1-p1)
Downgrading magento/module-inventory-requisition-list (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-admin-ui (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-api (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-shipping-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-source-selection-api (1.4.2 => 1.4.1-p1)
Downgrading magento/module-inventory-wishlist (1.0.2 => 1.0.1)
Downgrading magento/module-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-re-captcha-checkout-sales-rule (1.1.1 => 1.1.0)
Downgrading magento/module-re-captcha-customer (1.1.3 => 1.1.2)
Downgrading magento/module-re-captcha-frontend-ui (1.1.3 => 1.1.2)
Downgrading magento/module-staging-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-two-factor-auth (1.1.4 => 1.1.3)
Removing magento/module-admin-adobe-ims (100.4.0)
```

<u>Résultats attendus</u> :

La mise à niveau de la version 2.4.4 vers 2.4.4-p1 génère les packages (modules) corrects pour la version 2.4.4-p1.

<u>Résultats réels</u> :

Lors de la mise à niveau de la version 2.4.4 vers 2.4.4-p1, les versions (modules) de ces packages se dégradent, mais ces messages peuvent être ignorés et la fonctionnalité n’est pas affectée.

### Scénario 2

<u>Étapes à reproduire</u> :

Lorsque 2.4.4 les commerçants exécutent la commande `composer update`, les mêmes modules (modules) répertoriés ci-dessus dans **Scénario 1** sont mis à niveau vers leurs versions plus récentes, qui sont compatibles uniquement avec la version 2.4.5 et ne sont pas censées être utilisées avec la version 2.4.4.

<u>Résultats attendus</u> :

La mise à niveau de la version 2.4.4 vers 2.4.4-p1 génère les packages (modules) corrects pour la version 2.4.4-p1.

<u>Résultats réels</u> :

Les modules (modules) sont mis à niveau de la version 2.4.4 à la version 2.4.4-p1.

## Solution 1 : correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier ou cliquez sur le lien suivant : [Téléchargez ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip)

## Versions Adobe Commerce et Magento Open Source compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.4.4
* Adobe Commerce sur site 2.4.4
* Magento Open Source 2.4.4

>[!NOTE]
>
>Le correctif n’est pas compatible avec les autres versions et éditions Adobe Commerce et Magento Open Source.

## Comment appliquer le correctif

Utilisez le script bash joint [ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip) comme solution à ce problème.

**Instructions exactes sur l&#39;utilisation du script :**

### Sur Adobe Commerce sur l’infrastructure cloud :

1. Téléchargez le fichier de script bash `ACPLTSRV-2017-fix.sh` vers votre extraction locale de votre base de code cloud.
1. Exécutez le fichier de script bash `ACPLTSRV-2017-fix.sh` pour modifier les fichiers de compositeur localement.
1. Ajoutez et validez les fichiers de compositeur modifiés dans votre référentiel git.

### Sur Adobe Commerce ou Magento Open Source sur site :

1. Placez le script bash `ACPLTSRV-2017-fix.sh` dans le dossier `root` de votre installation Adobe Commerce/Magento Open Source 2.4.4 (le même dossier que `composer.json`).
1. Exécutez le script bash avec un argument `apply` pour verrouiller les modules concernés (modules) sur leurs versions 2.4.4 :

   ```bash
   sh ACPLTSRV-2017-fix.sh apply
   ```

1. Exécutez la mise à jour du compositeur pour installer les packages verrouillés (modules).
1. Une fois que vous êtes prêt à effectuer la mise à niveau vers la version 2.4.5 ou 2.4.4-p1, exécutez le script avec un argument `rollback` :

   ```bash
   sh ACPLTSRV-2017-fix.sh rollback
   ```

   Si vous ignorez cette étape, des erreurs de mise à niveau seront générées en raison des exigences de packages (modules) en conflit.
1. Une fois les étapes ci-dessus terminées, vous pouvez commencer la mise à niveau.

## Solution 2

La deuxième solution à ce problème consiste à ne pas exécuter la commande `composer update` sans argument.
