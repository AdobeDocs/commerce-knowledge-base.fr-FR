---
title: "ACSD-45488 : produit configurable avec plusieurs sources qui ne sont pas automatiquement retournées en stock"
description: Le correctif ACSD-45488 résout le problème en raison duquel un produit configurable avec plusieurs sources n’est pas automatiquement renvoyé en stock. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 est installé. L’ID de correctif est ACSD-45488. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: 83332226-b14e-4d36-bf65-170f55fff270
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-45488 : le produit configurable avec plusieurs sources qui ne sont pas retournées en stock automatiquement

Le correctif ACSD-45488 résout le problème en raison duquel un produit configurable avec plusieurs sources n’est pas automatiquement renvoyé en stock. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.18 est installée. L’ID de correctif est ACSD-45488. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un produit configurable avec plusieurs sources n’est pas automatiquement renvoyé en stock.

<u>Étapes à reproduire</u>:

1. Créez une source de stock secondaire.
1. Créez un produit configurable avec deux produits virtuels associés.
1. Attribuez les produits associés à la source de stock par défaut et définissez la quantité sur une.
1. Vérifiez les `stock_status` de `cataloginventory_stock_status`.
1. Définir les deux produits associés à *en rupture de stock*.
1. Vérifiez les `stock_status` de `cataloginventory_stock_status`.
1. Définir les deux produits associés *en stock*.
1. Vérifiez les `stock_status` de `cataloginventory_stock_status`.

<u>Résultats attendus</u>:

L’état du stock du produit configurable est mis à jour vers *en stock* lorsque les produits associés sont définis pour être en stock.

<u>Résultats réels</u>:

L’état du stock du produit configurable n’est pas mis à jour vers *en stock* lorsque les produits associés sont définis pour être en stock.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
