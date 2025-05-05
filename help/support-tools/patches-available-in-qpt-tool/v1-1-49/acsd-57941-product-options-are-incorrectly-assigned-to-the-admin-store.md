---
title: "ACSD-57941 : les options du produit sont incorrectement attribuées à l’admin store"
description: Appliquez le correctif ACSD-57941 pour résoudre le problème Adobe Commerce en raison duquel les options de produit sont incorrectement attribuées à l’admin store au lieu de leurs magasins respectifs.
feature: Products
role: Admin, Developer
source-git-commit: 1cc673716b75bda6cfe7b3d597ec94e4510fa7e4
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# ACSD-57941 : les options du produit sont incorrectement attribuées à l’admin store

Le correctif ACSD-57941 corrige le problème en raison duquel les options de produit sont incorrectement attribuées à l’admin store au lieu de leurs magasins respectifs. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 est installé. L’ID de correctif est ACSD-57941. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les options de produit sont incorrectement affectées à la boutique d’administrateurs au lieu de leurs magasins respectifs.

<u>Étapes à reproduire</u> :

1. Créez un produit simple.
1. Importez le même produit avec quelques options personnalisées.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et ouvrez le produit créé. Cliquez sur **[!UICONTROL Customizable options]** et vérifiez que les options importées sont visibles.
1. Importez le même fichier plusieurs fois de plus.

<u>Résultats attendus</u> :

Les options personnalisées sont mises à jour.

<u>Résultats réels</u> :

Les options personnalisées du produit sont dupliquées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
