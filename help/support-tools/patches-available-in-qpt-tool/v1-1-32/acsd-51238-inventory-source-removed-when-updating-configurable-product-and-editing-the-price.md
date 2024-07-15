---
title: "ACSD-51238 : La source de l’inventaire est supprimée lors de la mise à jour d’un produit configurable et de la modification du prix"
description: Appliquez le correctif ACSD-51238 pour résoudre le problème Adobe Commerce en raison duquel la source d’inventaire est supprimée lors de la mise à jour d’un produit configurable et de la modification du prix.
exl-id: ab2f60fd-5da3-45f7-a489-6f4f9d34e1f1
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51238 : La source du stock est supprimée lors de la mise à jour d’un produit configurable et de la modification du prix.

Le correctif ACSD-51238 corrige le problème en raison duquel la source d’inventaire est supprimée lors de la mise à jour d’un produit configurable et de la modification du prix. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.32 est installé. L’ID de correctif est ACSD-51238. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La source d’inventaire est supprimée lors de la mise à jour d’un produit configurable et de la modification du prix.

<u>Étapes à reproduire</u> :

1. Installer **[!DNL Adobe Commerce]** avec **[!DNL Inventory module]**
1. Accédez à **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** et créez *deux sources* et *deux stocks*.
1. Créez un **[!UICONTROL configurable product]** et affectez-le à **[!UICONTROL default sources]** ou **[!UICONTROL newly created sources]**.
1. Cliquez sur le **[!UICONTROL next button]** et *enregistrez* le produit.
1. Modifiez maintenant le même **[!UICONTROL Configurable Product]** et cliquez sur **[!UICONTROL Edit Configuration]** dans le **[!UICONTROL Configuration tab]**.
1. Dans `Step 3: Bulk Images,Price and Quantity`, remplacez `price` et laissez `Quantity` et `Images` sur `Skip quantity at this time` et `Skip image uploading at this time` respectivement.
1. Cliquez sur **[!UICONTROL next button]** et générez le produit.

<u>Résultats attendus</u>

La quantité par source à l’intérieur de **[!UICONTROL Configuration tab]** ne doit pas être vide.

<u>Résultats réels</u>

La quantité par source à l’intérieur de **[!UICONTROL Configuration tab]** est vide.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide [!DNL Quality Patches Tool].
