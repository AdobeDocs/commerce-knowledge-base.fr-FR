---
title: "ACSD-52095 : La gestion de la valeur du stock est incorrecte lors de l’exportation au format CSV"
description: Appliquez le correctif ACSD-52095 pour résoudre le problème Adobe Commerce en raison duquel la valeur du stock de gestion du produit est incorrecte lors de l’exportation au format CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095 : [!UICONTROL Manage Stock] valeur erronée lors de l’exportation d’un fichier CSV

Le correctif ACSD-52095 corrige le problème lorsque la valeur du produit `manage_stock` est incorrecte lors de l’exportation du fichier CSV. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.35 est installé. L’ID de correctif est ACSD-52095. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La valeur `manage_stock` est incorrectement définie sur 0 dans le fichier CSV après l’exportation du produit.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** et définissez **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Créez un produit et enregistrez-le.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Sélectionnez *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* et exportez les produits.
1. Vérifiez le fichier CSV généré : `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Accédez à nouveau à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** et définissez **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. Accédez à **Système** > **Exporter**.
Sélectionnez *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Vérifiez le fichier CSV généré : `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Ouvrez le produit dans l’Admin, accédez à **[!UICONTROL Advanced Inventory]** et vérifiez la valeur **[!UICONTROL Manage Stock]**.

<u>Résultats attendus</u>

La valeur **[!UICONTROL Manage Stock]** est *1* lorsqu’elle est activée pour les produits.

<u>Résultats réels</u>

La valeur **[!UICONTROL Manage Stock]** est *0* lorsqu’elle est activée pour les produits.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr>) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr>) dans le guide [!DNL Quality Patches Tool].
