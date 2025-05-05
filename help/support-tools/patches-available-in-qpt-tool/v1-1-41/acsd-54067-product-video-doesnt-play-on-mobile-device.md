---
title: "ACSD-54067 : la vidéo du produit ne s’exécute pas sur un appareil mobile"
description: Appliquez le correctif ACSD-54067 pour résoudre le problème Adobe Commerce en raison duquel une vidéo de produit n’est pas lue sur un appareil mobile.
feature: Media, Products
role: Admin, Developer
exl-id: 369650ef-bcce-47c5-bbfe-39f3c2b1d73f
source-git-commit: 0795e3e0ba11002c8aff2794e16fa05f1c7e19c3
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-54067 : La vidéo du produit ne s’exécute pas sur un appareil mobile

Le correctif ACSD-54067 corrige le problème lorsqu’une vidéo de produit n’est pas lue sur un appareil mobile. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 est installé. L’ID de correctif est ACSD-54067. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La lecture d’une vidéo de produit ne s’effectue pas sur un appareil mobile.

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce.
1. Exécutez la commande :
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Accédez à la page **[!UICONTROL Admin product list]** et filtrez selon *[!UICONTROL SKU product_dynamic_120]*.
1. Ouvrez la page produit et accédez à **[!UICONTROL Images and Videos]** > ajoutez une vidéo > remplissez l’URL : https://vimeo.com/347119375 et enregistrez.
1. Accédez au storefront et ouvrez la page de produit pour *[!UICONTROL product_dynamic_120]*.
1. Définissez le navigateur sur *mobile device* avec une largeur de *320px* et actualisez-le.
1. Dans le curseur de la galerie, sélectionnez la vidéo et cliquez pour la lire.

<u>Résultats attendus</u> :

La vidéo du produit est lue.

<u>Résultats réels</u> :

La vidéo du produit ne s’affiche pas.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
