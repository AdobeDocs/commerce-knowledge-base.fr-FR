---
title: "ACSD-45488 : produit configurable avec plusieurs sources qui ne sont pas automatiquement retournées en stock"
description: Le correctif ACSD-45488 résout le problème en raison duquel un produit configurable avec plusieurs sources n’est pas automatiquement renvoyé en stock. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 est installé. L’ID de correctif est ACSD-45488. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: 83332226-b14e-4d36-bf65-170f55fff270
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-45488 : le produit configurable avec plusieurs sources qui ne sont pas retournées en stock automatiquement

Le correctif ACSD-45488 résout le problème en raison duquel un produit configurable avec plusieurs sources n’est pas automatiquement renvoyé en stock. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.18 est installé. L’ID de correctif est ACSD-45488. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un produit configurable avec plusieurs sources n’est pas automatiquement renvoyé en stock.

<u>Étapes à reproduire</u> :

1. Créez une source de stock secondaire.
1. Créez un produit configurable avec deux produits virtuels associés.
1. Attribuez les produits associés à la source de stock par défaut et définissez la quantité sur une.
1. Vérifiez le `stock_status` de `cataloginventory_stock_status`.
1. Définissez les deux produits associés sur *out of stock*.
1. Vérifiez le `stock_status` de `cataloginventory_stock_status`.
1. Définissez les deux produits associés sur *en stock*.
1. Vérifiez le `stock_status` de `cataloginventory_stock_status`.

<u>Résultats attendus</u> :

L’état du stock du produit configurable est mis à jour sur *en stock* lorsque les produits associés sont définis pour être en stock.

<u>Résultats réels</u> :

L’état du stock du produit configurable n’est pas mis à jour vers *en stock* lorsque les produits associés sont définis pour être en stock.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
