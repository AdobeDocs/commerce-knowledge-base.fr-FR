---
title: Lenteur des performances, lenteur et longueur des fils
description: Cet article décrit comment résoudre les problèmes de performances du site et les problèmes d’exécution lente et bloquée causés par l’activation des tables plats et des indexeurs.
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Lenteur des performances, lenteur et longueur des fils

>[!WARNING]
>
>Dans n’importe quelle version d’Adobe Commerce, parce que certaines extensions ne fonctionnent qu’avec des tables plats, il existe un risque si vous désactivez les tables plats. Si vous savez que certaines extensions utilisent des indexeurs de catalogue plat, vous devrez peut-être en tenir compte lors de la définition de ces valeurs sur &quot;*Non*&quot;.

Cet article décrit comment résoudre les problèmes de performances du site et les problèmes d’exécution lente et de blocage causés par l’activation de [tables plates et indexeurs](https://docs.magento.com/m2/ce/user_guide/catalog/catalog-flat.html).

PRODUITS ET VERSIONS AFFECTÉS

* Adobe Commerce sur l’infrastructure cloud 2.1.x et versions ultérieures
* Adobe Commerce on-premise 2.1.x et versions ultérieures
* Magento Open Source 2.1.x et versions ultérieures

## Problème

Les indexeurs plats peuvent provoquer :

* Problèmes de chargement SQL lourd et de performances du site.
* Longue course et crons coincés.

## Cause

Tables plats et indexeurs activés.

## Solution {#solution}

À compter d’Adobe Commerce et de Magento Open Source 2.1.x, l’utilisation d’un catalogue plat n’est plus une bonne pratique et n’est pas recommandée. L’utilisation continue de cette fonctionnalité provoque une dégradation des performances et d’autres problèmes d’indexation. Pour désactiver le catalogue plat :

1. Dans l’administrateur, accédez à **Magasins** > **Paramètres** > **Configuration**.
1. Dans le panneau de gauche sous **Catalog** , choisissez **Catalog**.
1. Développez la section **Storefront** et procédez comme suit :
   * Définissez **Utiliser la catégorie de catalogue plat** sur *Non*.
   * Définissez **Utiliser le produit de catalogue plat** sur *Non*.
1. Une fois l’opération terminée, cliquez sur **Enregistrer la configuration**. Lorsque vous y êtes invité, actualisez ensuite le cache.
1. Videz le cache en exécutant `php bin/magento cache:flush`.

Si vous ne pouvez pas modifier les **Utiliser la catégorie de catalogue plat** et **Utiliser le produit de catalogue plat** en *Non*, car les options sont grisées, désactivez les indexeurs plats dans `app/etc/config.php` :

1. Exécutez cette commande pour vous assurer que tous les indexeurs sont définis sur Mise à jour par planning : `php bin/magento indexer:set-mode schedule`.
1. Modifiez `app/etc/config.php` et localisez les lignes avec `flat_catalog_product` et `flat_catalog_category` - remplacez-les de 1 à 0 pour les désactiver.
1. Exécutez la commande `php bin/magento app:config:import`
1. Exécutez cette commande pour confirmer que les indexeurs plats sont désactivés : `php        bin/magento indexer:status`.
1. Videz le cache en exécutant `php bin/magento cache:flush`.

## Informations connexes

[Réinitialisez manuellement les tâches Adobe Commerce cron bloquées sur Cloud](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md) dans notre base de connaissances de support.
