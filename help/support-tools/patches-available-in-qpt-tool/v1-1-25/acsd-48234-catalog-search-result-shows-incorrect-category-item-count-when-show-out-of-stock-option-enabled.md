---
title: 'ACSD-48234 : résultat de la recherche catalogue : nombre d’éléments de catégorie incorrect lorsque [!UICONTROL Display Out of Stock Products] activé'
description: Appliquez le correctif ACSD-48234 pour résoudre le problème Adobe Commerce en raison duquel le résultat de la recherche catalogue affiche un nombre d’éléments de catégorie incorrect lorsque l’option [!UICONTROL Display Out of Stock Products] est activée.
exl-id: 8e70fe73-d550-4e11-b25e-84955e136d12
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48234 : les résultats de recherche catalogue affichent un nombre d’éléments de catégorie incorrect **[!UICONTROL Display Out of Stock Products]** activé

Le correctif ACSD-48234 résout le problème où le résultat de la recherche catalogue affiche un nombre d’éléments de catégorie incorrect lorsque l’option **[!UICONTROL Display Out of Stock Products]** est activée. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 est installé. L’ID de correctif est ACSD-48234. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.


## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le résultat de la recherche catalogue affiche un nombre d’éléments de catégorie incorrect lorsque l’option **[!UICONTROL Display Out of Stock Products]** est activée.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** et ouvrez l’attribut **[!UICONTROL color]** .
1. Ajoutez deux options, par exemple orange et vert. Enregistrez l’attribut .
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** et ajoutez l’attribut **[!UICONTROL color]** au jeu d’attributs **[!UICONTROL Default]**.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** et définissez **[!UICONTROL Display Out of Stock Products]** sur _Oui_.
1. Créez la catégorie &quot;cat1&quot;.
1. Créez deux produits :
   1. Nom : prod1, Color : orange, Catégories : cat1.
   1. Nom : prod2, Couleur : vert, Catégories : cat1.
1. Ouvrez la catégorie cat1 sur le storefront.
1. Sélectionnez la couleur orange dans la navigation superposée.

<u>Résultats attendus</u> :

Seul le produit prod1 s’affiche.

<u>Résultats réels</u> :

Les produits prod1 et prod2 s’affichent.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
