---
title: "MDVA-34665 : les produits du bundle disparaissent de la page de catégorie storefront"
description: Le correctif MDVA-34665 corrige le problème lié à l’absence de produits regroupés sur les pages de catégorie. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 est installé. L’ID de correctif est MDVA-34665. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.
exl-id: 2b393f91-de0d-4c54-89db-5e2af13f93a6
feature: Categories, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# MDVA-34665 : les produits du bundle disparaissent de la page de catégorie storefront

Le correctif MDVA-34665 corrige le problème lié à l’absence de produits regroupés sur les pages de catégorie. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 est installé. L’ID de correctif est MDVA-34665. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.4-2.3.4-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

**Cas 1 :**

<u>Conditions préalables</u> :

1. Créez 15 000 produits regroupés avec un seul produit comme option de regroupement. N’utilisez pas le même produit simple avec plusieurs produits regroupés.
1. Les produits simples doivent être définis sur *Non visibles individuellement*.

<u>Étapes à reproduire</u> :

1. Attribuez 15 000 produits regroupés en deux catégories, soit 7 500 produits chacun.
1. Sélectionnez tous les produits simples (15k) et mettez à jour le stock à l’aide de mises à jour d’attributs de masse de produit. Notre objectif est d’avoir de nombreux identifiants dans la table cl de recherche (les tables cl sont les tables utilisées par l’indexeur pour savoir quels enregistrements doivent être mis à jour.)
1. Assurez-vous que la table `catalogsearch_fulltext_cl` contient 15 000 identifiants.
1. Assurez-vous que l&#39;indexeur `indexer_update_all_views` est exécuté.
1. Interrogez continuellement la page de catégorie et observez le nombre de produits.

<u>Résultats attendus</u> :

Le nombre de produits doit rester tel qu’il était après la réindexation.

<u>Résultats réels</u> :

Le nombre de produits chute à 7 450 au bout d’un certain temps. Il reste dans 7 450 même une fois l’indexation terminée.

**Cas 2 :**

<u>Étapes à reproduire</u> :

1. Créez un lot de produits avec un produit simple associé comme option.
1. Remplacez les modes de l&#39;indexeur par *mettre à jour selon la planification*.
1. Affectez le produit du lot à une catégorie.
1. Remplacez l’état du stock du produit simple par *out of stock*.
1. Exécutez cron ; le produit du lot disparaît du storefront.
1. Ajoutez le stock au produit simple et enregistrez.
1. Exécutez l’indexeur cron.
1. Actualisez la page de catégorie.

<u>Résultats attendus</u> :

Le produit est toujours absent.

<u>Résultats réels</u> :

Le produit groupé réapparaît.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
