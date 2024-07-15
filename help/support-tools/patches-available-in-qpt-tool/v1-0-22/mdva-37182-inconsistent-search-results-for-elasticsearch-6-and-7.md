---
title: 'MDVA-37182 : résultats de recherche incohérents dans Elasticsearch 6 et 7'
description: Le correctif MDVA-37182 corrige le problème avec un comportement de recherche incohérent entre les versions 6 et 7 de l’Elasticsearch. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 est installé. L’ID de correctif est MDVA-37182. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: 6c4e2d2f-cced-487d-b253-fd0c80bc6067
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-37182 : résultats de recherche incohérents dans Elasticsearch 6 et 7

Le correctif MDVA-37182 corrige le problème avec un comportement de recherche incohérent entre les versions 6 et 7 de l’Elasticsearch. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 est installé. L’ID de correctif est MDVA-37182. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.4.1-2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Comportement de recherche incohérent.

<u>Étapes à reproduire</u> :

1. Créez des produits avec les détails suivants :
   * Noms : &quot;5127AC&quot;, &quot;5127SS&quot;, &quot;5127AB&quot;
   * SKU : &quot;product1&quot;, &quot;product2&quot;, &quot;product3&quot;
1. Définissez le moteur de recherche sur Elasticsearch 6 (ES6).
1. Exécutez la réindexation complète.
1. Sur le storefront, recherchez &quot;5127s&quot;.
1. Définissez le moteur de recherche sur Elasticsearch 7 (ES7).
1. Exécutez la réindexation complète.
1. Sur le storefront, recherchez &quot;5127s&quot;.

<u>Résultat réel :</u> :

ES6 : la recherche ne renvoie aucun résultat. ES7 : la recherche renvoie trois produits.

<u>Résultat attendu :</u> :

La recherche renvoie un produit pour les deux versions.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants, en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
