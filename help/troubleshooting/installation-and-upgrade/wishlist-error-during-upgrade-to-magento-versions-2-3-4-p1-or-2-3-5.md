---
title: Erreur de liste de souhaits lors de la mise à niveau vers Adobe Commerce versions 2.3.4-p1 ou 2.3.5
description: Cet article fournit un correctif pour le problème connu lors de la mise à niveau vers les versions 2.3.4-p1 et 2.3.5 d’Adobe Commerce liées à une erreur de liste de souhaits lors de la mise à niveau vers ces versions.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%
---
# Erreur de liste de souhaits lors de la mise à niveau vers Adobe Commerce versions 2.3.4-p1 ou 2.3.5

Cet article fournit un correctif pour le problème connu lors de la mise à niveau vers les versions 2.3.4-p1 et 2.3.5 d’Adobe Commerce liées à une erreur de liste de souhaits lors de la mise à niveau vers ces versions.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud 2.3.4-p1 et 2.3.5
* Adobe Commerce on-premise 2.3.4-p1 et 2.3.5

## Problème

Lors de la mise à niveau de votre Adobe Commerce (toutes les méthodes de déploiement) et de Magento Open Source vers la version 2.3.5 ou 2.3.4-p1, vous pouvez obtenir une erreur de liste de souhaits (détaillée ci-dessous) à partir du module :

```php
Magento_Wishlist
```

La mise à niveau d’Adobe Commerce (toutes les méthodes de déploiement)/Magneto Open Source version 2.3.4-p1 **vers la version 2.3.4-p2** ou d’Adobe Commerce (toutes les méthodes de déploiement)/Magneto Open Source version 2.3.5 **vers la version 2.3.5-p1** corrige l’erreur.

<u>Procédure à suivre </u> :

Mettez à niveau votre Adobe Commerce (toutes les méthodes de déploiement)/Magento Open Source vers la version 2.3.4-p1 ou 2.3.5.

<u>Résultat attendu </u> :

Le processus de mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement)/Magento Open Source version 2.3.4-p1 ou 2.3.5 se termine normalement.

<u>Résultat réel</u> :

Lors de la mise à niveau, vous obtenez cette erreur :

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Solutions

* Si vous effectuez une mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement)/Magneto Open Source version 2.3.5, **effectuez une mise à niveau vers la version 2.3.5-p1**. Adobe Commerce (toutes les méthodes de déploiement)/Magento Open Source version 2.3.5-p1 remplace 2.3.5.
* Si vous effectuez une mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement)/Magento Open Source version 2.3.4-p1, **effectuez une mise à niveau vers version 2.3.4-p2**. Adobe Commerce (toutes les méthodes de déploiement)/Magneto Open Source version 2.3.4-p2 remplace la version 2.3.4-p1.

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [Guide d’Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/overview)
* [Adobe Commerce sur les infrastructures cloud - Mise à niveau de la version d’Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [Adobe Commerce On-premise Et Magento Open Source - Mettez à niveau l’application et les modules Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-operations/upgrade-guide/overview)
* [Page de configuration des éléments de liste de souhaits](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts#wishlist-item-configure-page)
* [Modules fournissant des rapports avancés](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
