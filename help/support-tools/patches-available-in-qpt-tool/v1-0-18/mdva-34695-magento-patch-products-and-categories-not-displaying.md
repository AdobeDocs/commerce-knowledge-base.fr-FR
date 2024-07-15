---
title: "MDVA-34695 : Produits et catégories non affichés"
description: Le correctif MDVA-34695 résout le problème en raison duquel les produits et les catégories ne s’affichent pas dans la grille des catégories dans Admin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 est installé. L’ID de correctif est MDVA-34695. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.
exl-id: 0c2e50c1-648b-480a-a768-72af721950d8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-34695 : Produits et catégories non affichés

Le correctif MDVA-34695 résout le problème en raison duquel les produits et les catégories ne s’affichent pas dans la grille des catégories dans Admin. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 est installé. L’ID de correctif est MDVA-34695. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.4

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.0-2.4.0-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des valeurs négatives pour `children_count` apparaissent dans la base de données après la suppression de catégories.

<u>Étapes à reproduire</u> :

1. Connectez-vous au serveur principal Admin.
1. Accédez à **Catalogue > Catégories**.
1. Cliquez sur **Ajouter une sous-catégorie**.
1. Définissez **nom de catégorie** = *Parent 1*, puis enregistrez.
1. Cliquez sur **Ajouter une sous-catégorie**.
1. Définissez **nom de catégorie** = *enfant 1*, puis enregistrez.
1. Cliquez sur **Ajouter une sous-catégorie**.
1. Définissez **nom de catégorie** = *Enfant 2*, puis enregistrez.
1. Cliquez sur **Ajouter une sous-catégorie**.
1. Définissez **nom de catégorie** = *enfant 3*, puis enregistrez. À ce stade, cette catégorie doit avoir un niveau = *5*.
1. Cliquez sur la catégorie **Enfant 1** .
1. Supprimez la catégorie.

<u>Résultats attendus</u> :

La grille Catégories affiche les produits et les catégories, comme prévu.

<u>Résultats réels</u> :

La grille de catégories est vide. Vérifiez la table `catalog_category_entity` dans la base de données. Notez que `children_count` est devenu négatif.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
