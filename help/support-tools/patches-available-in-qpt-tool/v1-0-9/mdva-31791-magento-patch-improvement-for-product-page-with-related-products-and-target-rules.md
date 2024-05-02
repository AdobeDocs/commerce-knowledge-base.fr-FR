---
title: 'Correctif MDVA-31791 : amélioration de la page produit avec les produits associés et les règles de ciblage'
description: Le correctif MDVA-31791 améliore les performances des pages de produits, lorsque [Produits associés](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) ou [Règles de produits associés](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (règles cibles) sont utilisés. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.1.
exl-id: e737bccb-d9eb-4794-9d6b-2c22fa8edaa2
feature: Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# Correctif MDVA-31791 : amélioration de la page produit avec les produits associés et les règles cibles.

Le correctif MDVA-31791 améliore les performances des pages de produits, lorsque [Produits associés](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) ou [Règles de produits connexes](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (règles de ciblage) sont utilisées. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.9 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.1.

## Produits et versions concernés

**Le correctif a été créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.0

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.4, 2.3.4-p1, 2.3.4-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Faibles performances des pages de produits si des produits associés ou des règles Target sont utilisés.

Pensez à appliquer le correctif MDVA-31791 si vous utilisez [Produit associé](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) ou [Règles de produit connexes](https://docs.magento.com/user-guide/marketing/product-related-rules.html) .

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
