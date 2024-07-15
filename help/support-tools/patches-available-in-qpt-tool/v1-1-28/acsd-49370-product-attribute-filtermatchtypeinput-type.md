---
title: "ACSD-49370 : l’attribut de produit a le type 'FilterMatchTypeInput' dans le schéma GraphQL"
description: Appliquez le correctif ACSD-49370 pour résoudre le problème Adobe Commerce où l’attribut de produit a un type "FilterMatchTypeInput" dans le schéma GraphQL.
exl-id: 132eee3a-30b0-4810-b2f0-0d05d0a9f009
feature: Admin Workspace, Attributes, GraphQL, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-49370 : l’attribut de produit est de type `FilterMatchTypeInput` dans le schéma GraphQL

Le correctif ACSD-49370 corrige le problème lorsque l’attribut de produit a un type `FilterMatchTypeInput` dans le schéma GraphQL. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 est installé. L’ID de correctif est ACSD-49370. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut de produit a un type `FilterMatchTypeInput` dans le schéma GraphQL.

<u>Étapes à reproduire</u> :

1. Créez l’attribut de produit *Date et heure*.

   * [!UICONTROL Type] : [!UICONTROL DateTime]
   * [!UICONTROL Default Label] : [!UICONTROL Date Time]
   * [!UICONTROL Use in Search] : [!UICONTROL Yes]
   * [!UICONTROL Visible in Advanced Search] : [!UICONTROL Yes]

1. Recherchez la documentation *API GQL* pour la définition de type `ProductAttributeFilterInput`.
1. Observez le type d’entrée pour l’attribut créé.

<u>Résultats attendus</u> :

L’attribut *Date Time* affiche le type d’entrée de filtre `FilterRangeTypeInput`.

<u>Résultats réels</u> :

L’attribut *Date Time* affiche le type d’entrée de filtre `FilterMatchInputType`.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
