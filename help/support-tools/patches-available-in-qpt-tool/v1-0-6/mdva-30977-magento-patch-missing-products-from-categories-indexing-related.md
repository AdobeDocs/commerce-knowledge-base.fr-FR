---
title: '''MDVA-30977 : produits manquants dans les catégories, liés à l''indexation'''
description: Le correctif MDVA-30977 corrige les problèmes liés aux produits affichés sur les pages de catégorie storefront lors de la réindexation ou des actions de masse avec un grand nombre de produits. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 est installé. Les problèmes doivent être résolus dans Adobe Commerce 2.4.2.
exl-id: 66ec4f53-c01d-4f87-a175-84f44a26f5d3
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# MDVA-30977 : produits manquants dans les catégories, indexage lié

Le correctif MDVA-30977 corrige les problèmes liés aux produits affichés sur les pages de catégorie storefront lors de la réindexation ou des actions de masse avec un grand nombre de produits. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 est installé. Les problèmes doivent être résolus dans Adobe Commerce 2.4.2.

## Produits et versions concernés

Le correctif a été créé pour Adobe Commerce sur l’infrastructure cloud 2.3.4. Il est également compatible avec Adobe Commerce on-premise 2.3.4.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problèmes

### Problème 1

Le nombre de produits affichés sur la page de catégorie sur le storefront est différent après chaque rechargement de page lors de la mise à jour des produits en masse.

<u>Étapes à reproduire :</u>

1. Créez au moins 30 000 produits dans deux catégories - au moins 15 000 produits dans chaque catégorie.
1. Accédez à **Catalogue** > **Produits** dans l’administrateur Commerce.
1. Sélectionnez tous les produits de la grille et effectuez une mise à jour des attributs en masse. Par exemple, définissez l’attribut **New** = *Yes* .
1. Exécutez deux fois la tâche cron Magento à l’aide de la commande `bin/magento cron:run`.
1. Actualisez les pages de catégorie sur Storefront pendant qu’Adobe Commerce effectue la mise à jour de 30 000 produits.

<u>Résultat attendu :</u>

Le nombre de produits des catégories est toujours de 15 000 sur chaque actualisation de page de catégorie.

<u>Résultat réel :</u>

Le nombre de produits des catégories est différent pour chaque actualisation de page de catégorie.

### Problème 2

Lorsque la réindexation complète de l’inventaire est exécutée, les pages de catégorie deviennent vides et le message *Nous ne pouvons pas trouver de produits correspondant à la sélection* s’affiche.

<u>Étapes à reproduire :</u>

1. Configurez Adobe Commerce avec Elasticsearch.
1. Ajoutez un nouveau site web.
1. Créez une source et affectez-la au nouveau site web à l’aide de l’option Gérer le stock.
1. Créez 30 000 produits configurables.
1. Affectez tous les produits au nouveau site web et ajoutez également l’inventaire à la nouvelle source d’inventaire.
1. Exécutez une réindexation complète.
1. Exécutez la réindexation de l’inventaire en exécutant `bin/magento indexer:reindex inventory`
1. Parcourez une catégorie comportant un grand nombre de produits.

<u>Résultat attendu :</u>

Les pages de catégorie affichent les produits comme vous le faites habituellement lors de la réindexation.

<u>Résultat réel :</u>

Les pages de catégorie deviennent vides lors de la réindexation.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
