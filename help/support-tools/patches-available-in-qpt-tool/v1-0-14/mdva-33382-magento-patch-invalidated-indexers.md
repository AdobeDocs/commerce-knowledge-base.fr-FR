---
title: 'Correctif ''MDVA-33382 : indexeurs invalidés'''
description: Le correctif MDVA-33382 résout le problème lorsque les indexeurs sont invalidés après l’ajout, la suppression ou la réorganisation de produits dans une catégorie. Les indexeurs invalidés sont `catalog_category_product` , `catalogsearch_fulltext` (et leurs dépendances).
exl-id: b4ac10ee-0f9d-4d7a-be72-c4d90ebadb10
feature: Catalog Management, Categories, Price Indexer
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Correctif MDVA-33382 : indexeurs invalidés

Le correctif MDVA-33382 résout le problème lorsque les indexeurs sont invalidés après l’ajout, la suppression ou la réorganisation de produits dans une catégorie. Les indexeurs invalidés sont `catalog_category_product` , `catalogsearch_fulltext` (et leurs dépendances).

Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 est installé. Veuillez noter que le problème sera corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u> :

1. Définissez tous les modes d&#39;indexeur d&#39;index sur **Mettre à jour selon le planning**.
1. Supprimez un produit d’une page de modification de catégorie.
1. Enregistrez la catégorie.
1. Vérifiez l’état des index dans le serveur principal ou dans l’interface de ligne de commande.

<u>Résultats attendus</u> :

Les index suivants ne sont pas invalidés : `catalog_category_product` , `catalogsearch_fulltext` (et leurs dépendances), comme prévu.

<u>Résultats réels</u> :

Les index suivants sont invalidés : `catalog_category_product` , `catalogsearch_fulltext` (et leurs dépendances).

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
