---
title: Erreur de liste blanche lors de la mise à niveau vers les versions 2.3.4-p1 ou 2.3.5 d’Adobe Commerce
description: Cet article fournit un correctif pour le problème connu lors de la mise à niveau vers Adobe Commerce versions 2.3.4-p1 et 2.3.5 lié à une erreur de liste bloquée lors de la mise à niveau vers ces versions.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Erreur de liste blanche lors de la mise à niveau vers les versions 2.3.4-p1 ou 2.3.5 d’Adobe Commerce

Cet article fournit un correctif pour le problème connu lors de la mise à niveau vers Adobe Commerce versions 2.3.4-p1 et 2.3.5 lié à une erreur de liste bloquée lors de la mise à niveau vers ces versions.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.3.4-p1 et 2.3.5
* Adobe Commerce on-premise 2.3.4-p1 et 2.3.5

## Problème

Lors de la mise à niveau de votre Adobe Commerce (toutes les méthodes de déploiement) et de votre Magento Open Source vers la version 2.3.5 ou 2.3.4-p1, vous pouvez obtenir une erreur de liste bloquée (détaillée ci-dessous) à partir du module :

```php
Magento_Wishlist
```

Mise à niveau depuis Adobe Commerce (toutes les méthodes de déploiement)/Magneto Open Source version 2.3.4-p1 **vers la version 2.3.4-p2** ou depuis Adobe Commerce (toutes les méthodes de déploiement)/Magneto Open Source version 2.3.5 **vers la version 2.3.5-p1** corrige l’erreur.

<u>Étapes à reproduire</u>:

Mettez à niveau votre Adobe Commerce (toutes les méthodes de déploiement)/Magento Open Source vers la version 2.3.4-p1 ou 2.3.5.

<u>Résultat attendu</u>:

Le processus de mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement)/Magento Open Source version 2.3.4-p1 ou 2.3.5 se termine normalement.

<u>Résultat réel</u>:

Pendant la mise à niveau, vous obtenez cette erreur :

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Solutions

* Si vous effectuez une mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement)/Magneto Open Source version 2.3.5, **mise à niveau vers la version 2.3.5-p1**. Adobe Commerce (toutes les méthodes de déploiement)/Magento Open Source version 2.3.5-p1 remplace 2.3.5.
* Si vous effectuez une mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement)/Magento Open Source version 2.3.4-p1, **mise à niveau vers la version 2.3.4-p2**. Adobe Commerce (toutes les méthodes de déploiement)/Magneto Open Source version 2.3.4-p2 remplace la version 2.3.4-p1.

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [Guide sur l’infrastructure cloud d’Adobe Commerce](https://devdocs.magento.com/cloud/bk-cloud.html)
* [Adobe Commerce sur l’infrastructure cloud - Mise à niveau de la version Adobe Commerce](https://devdocs.magento.com/cloud/project/project-upgrade.html)
* [Adobe Commerce On-Premise Et Magento Open Source - Mettez à niveau l’application et les modules Adobe Commerce](https://devdocs.magento.com/guides/v2.3/comp-mgr/bk-compman-upgrade-guide.html)
* [Page de configuration des éléments de liste blanche](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/layouts/product-layouts.html#wishlist-item-configure-page)
* [Modules proposant des rapports avancés](https://devdocs.magento.com/guides/v2.3/advanced-reporting/modules.html)
