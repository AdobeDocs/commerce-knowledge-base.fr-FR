---
title: "ACSD-50813 : impossible pour l’administrateur d’ajouter des produits groupés contenant une barre oblique"
description: Appliquez le correctif ACSD-50813 pour résoudre le problème de performances d’Adobe Commerce en raison duquel l’administrateur ne peut pas ajouter de produits regroupés contenant une barre oblique (&grave;/&grave;) dans le SKU avec la fonctionnalité *Ajouter des produits par SKU* dans l’ordre d’administration.
exl-id: 80dfe877-9dfd-44a9-9bf0-37e929642fc0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-50813 : L’administrateur ne peut pas ajouter de produits groupés contenant une barre oblique

Le correctif ACSD-50813 corrige le problème où l’administrateur ne peut pas ajouter de produits groupés contenant une barre oblique (`/`) dans le SKU avec la fonctionnalité *[!UICONTROL Add Products by SKU]* dans l’ordre d’administration. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.34 est installé. L’ID de correctif est ACSD-50813. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’administrateur ne peut pas ajouter à l’ordre d’administration des produits regroupés contenant une barre oblique (`/`) dans le SKU avec la fonctionnalité *[!UICONTROL Add Products by SKU]*.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Créez un produit simple.
1. Créez un produit fourni.
1. Ajoutez une barre oblique (`/`) au milieu du SKU (par exemple : *Bu/ndle*).
1. Ajoutez une option regroupée avec **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*.
1. Attribuez au moins un produit simple à l’option .
1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Orders]** et créez une nouvelle commande.
1. Cliquez sur **[!UICONTROL Add Products by SKU]**.
1. Saisissez votre SKU, puis cliquez sur **[!UICONTROL Add to Order]**.
1. Ouvrez la console du navigateur.
1. Cliquez sur **[!UICONTROL Configure]**.

<u>Résultats attendus</u> :

Il n’y a pas d’erreur.

<u>Résultats réels</u> :

Erreur JS dans la console :

*Erreur non interceptée : erreur de syntaxe, expression non reconnue : div[id=sku_bu/ndle]*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
