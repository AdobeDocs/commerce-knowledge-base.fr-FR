---
title: "ACSD-48293 : produits composites en rupture de stock lors de la vente de produits enfants redémarrés"
description: Appliquez le correctif ACSD-48293 pour résoudre le problème Adobe Commerce en raison duquel les produits composites sont en rupture de stock lorsque les produits enfants vendus sont renvoyés en stock.
exl-id: 74ca34fe-e015-4daf-a608-4756c8ab3558
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48293 : produits composites en rupture de stock lors de la vente de produits enfants redémarrés

Le correctif ACSD-48293 corrige le problème de rupture de stock des produits composites lorsque les produits enfants vendus sont retournés en stock. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 est installé. L’ID de correctif est ACSD-48293. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits composites sont en rupture de stock lorsque les produits enfants qui ont été vendus sont retournés en stock.

<u>Étapes à reproduire</u> :

1. Créez un site web secondaire, un magasin et une vue de magasin.
1. Créez deux sources et stocks et affectez-les à chaque site web.
1. Activez l’option Afficher les produits en rupture de stock sous **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Créez un produit configurable avec un produit associé à l’aide de la source de stock du site web principal (définissez la quantité = 1).
1. Commandez le produit configurable.
1. Lancez le cron.
1. Ouvrez le produit configurable à partir du storefront et vérifiez qu’il est en rupture de stock.
1. Ouvrez le produit configurable à partir de [!UICONTROL Admin] et définissez **[!UICONTROL Manage Stock Option]** sur *[!UICONTROL No]*.
1. Lancez le cron.
1. Livrez la commande et ajoutez une quantité au produit simple qui le fait en stock.
1. Lancez le cron.
1. Vérifiez la disponibilité du produit sur le storefront.

<u>Résultats attendus</u> :

Le produit configurable est en stock.

<u>Résultats réels</u> :

Le produit configurable est en rupture de stock.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
