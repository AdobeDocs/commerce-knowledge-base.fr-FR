---
title: "MDVA-36833 : pagination rompue sur la page des résultats de recherche"
description: Le correctif MDVA-36833 corrige le problème de pagination lorsque le catalogue partagé est activé et que certains produits étaient exclus du catalogue partagé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 est installé. L’ID de correctif est MDVA-36833. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: 7105c4ed-48d9-4d4c-bf12-5914bbad62da
feature: Catalog Management, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-36833 : pagination rompue sur la page des résultats de recherche

Le correctif MDVA-36833 corrige le problème de pagination lorsque le catalogue partagé est activé et que certains produits étaient exclus du catalogue partagé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 est installé. L’ID de correctif est MDVA-36833. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exclusion de certains produits du catalogue partagé entraîne une pagination rompue pour les résultats de recherche.

<u>Étapes à reproduire :</u>

1. Activez le catalogue partagé.
1. Accédez à **Catalogue** > **Catalogues partagés** et configurez le catalogue partagé par défaut en lui attribuant tous les produits.
1. Chargez le storefront et recherchez &quot;jacket&quot;.
1. Notez les produits répertoriés sur la première page. Il devrait y avoir 12 produits.
1. Notez 11 SKU à partir de la 1ère page. Accédez au serveur principal et chargez le catalogue partagé par défaut.
1. Annulez l’affectation des SKU précédemment notées du catalogue partagé par défaut.
1. Allez sur la vitrine et cherchez &quot;veste&quot;.
1. Consultez la première page des résultats de la recherche.

<u>Résultat réel :</u>

La première page comporte un produit et le reste des produits est disponible sur la deuxième page.

<u>Résultat attendu :</u>

La première page doit comporter 12 produits.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.


## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
