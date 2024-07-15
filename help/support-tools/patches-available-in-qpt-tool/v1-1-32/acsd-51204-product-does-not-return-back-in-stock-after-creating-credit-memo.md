---
title: "ACSD-51204 : le produit ne revient pas en stock après la création de l’avoir de crédit"
description: Appliquez le correctif ACSD-51204 pour résoudre le problème Adobe Commerce en raison duquel le produit ne revient pas en stock après la création de l’avoir.
feature: Orders, Products, Returns
role: Admin
exl-id: 302033bc-2ca5-40d6-b692-24ae46b21c31
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-51204 : le produit ne revient pas en stock après la création de l’avoir-mémoire de crédit

Le correctif ACSD-51204 corrige le problème en raison duquel le produit ne revient pas en stock après la création de l’avoir. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 est installé. L’ID de correctif est ACSD-51204. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit vendu ne revient pas en stock après la création de l’avoir.

<u>Étapes à reproduire</u> :

1. Installez **[!UICONTROL Adobe Commerce]** et activez les **[!UICONTROL Inventory Management Module]** avec les *source* et *stock* par défaut uniquement.
1. Ajoutez un **[!UICONTROL new product]** avec une quantité de *10*.
1. Affectez le produit à **[!UICONTROL default stock]**.
1. Sur le storefront, ajoutez le produit au panier et passez une commande pour une quantité disponible entière de 10.
1. Dans le panneau d’administration, générez une *facture* et une *livraison* pour la commande.
1. Créez un **[!UICONTROL Credit Memo]** avec la case à cocher *Revenir au stock* sélectionnée pour tous les éléments.
1. Vérifiez les **[!UICONTROL Salable Quantity]** du produit dans l’Admin.

<u>Résultats attendus</u> :

La quantité vendable du produit doit revenir à *10*.

<u>Résultats réels</u> :

La quantité vendable du produit est conservée sous la forme *0*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide [!DNL Quality Patches Tool].
