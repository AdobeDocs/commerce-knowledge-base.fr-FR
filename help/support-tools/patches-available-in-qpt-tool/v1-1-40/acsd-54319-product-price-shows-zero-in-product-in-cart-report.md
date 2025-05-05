---
title: 'ACSD-54319 : le prix du produit affiche zéro dans le *[!UICONTROL Products in Carts]* rapport'
description: Appliquez le correctif ACSD-54319 pour résoudre le problème Adobe Commerce où le prix du produit affiche zéro dans le rapport *[!UICONTROL Products in Carts]*.
feature: Reporting, Products
role: Admin, Developer
exl-id: f53b3ed3-d5d5-461c-bba2-4f9f3f038580
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-54319 : le prix du produit affiche zéro dans le rapport *[!UICONTROL Products in Carts]*

Le correctif ACSD-54319 corrige le problème où le prix du produit affiche zéro dans le rapport *[!UICONTROL Products in Carts]*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 est installé. L’ID de correctif est ACSD-54319. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix du produit affiche zéro dans le rapport *[!UICONTROL Products in Carts]*.

<u>Étapes à reproduire</u> :

1. Définissez **[!UICONTROL Catalog Price Scope]** sur **[!UICONTROL Website]** à partir de **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]**.
1. Créez un second site web à partir de **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Créez un produit à partir de **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Attribuez ce produit au deuxième site web uniquement.
1. Ajoutez un produit au panier à partir du deuxième site web.
1. Accédez à la grille **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]**.
1. Vérifiez la colonne *[!UICONTROL Price]* dans la grille *[!UICONTROL Products In Carts]*.

<u>Résultats attendus</u> :

Le prix du produit n’est pas nul dans la grille de rapports *[!UICONTROL Products in Carts]*.

<u>Résultats réels</u> :

Le prix du produit est zéro dans la grille de rapports *[!UICONTROL Products in Carts]*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
