---
title: 'ACSD-51497 : impossible de trier la page du catalogue par attribut personnalisé de type Liste déroulante'
description: Appliquez le correctif ACSD-51497 pour résoudre le problème Adobe Commerce en raison duquel un client ne peut pas trier une page de catalogue par attribut personnalisé de type Liste déroulante.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: 60a4f375-9b9a-4026-9dc7-d9f847a75656
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-51497 : impossible de trier la page du catalogue par attribut personnalisé de type *Liste déroulante*

Le correctif ACSD-51497 corrige le problème lorsqu’un client ne peut pas trier une page de catalogue par un attribut personnalisé de type *Dropdown*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 est installé. L’ID de correctif est ACSD-51497. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un client ne peut pas trier une page de catalogue par un attribut personnalisé de type *Liste déroulante*.

<u>Étapes à reproduire</u>

1. Créez environ six produits simples et affectez-les à une seule catégorie.
1. Créez un attribut de produit afin de l’ajouter en tant qu’option de tri sur les pages de liste.

   * Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * Dans l’onglet **[!UICONTROL Properties]** , définissez les options suivantes :

      * *[!UICONTROL Default Label]* = *test*
      * *[!UICONTROL Catalog Input Type]* pour le propriétaire du magasin = *Liste déroulante*
      * *[!UICONTROL Options]* :

         * *first*
         * *second*
         * *third*
         * *quatrième*

   * Dans l’onglet **[!UICONTROL Storefront Properties]** , définissez les options suivantes :

      * *[!UICONTROL Used for sorting in product listing]* = *Oui*
      * Laissez toutes les autres options *Par défaut*.

1. Attribuez l’attribut *test* à l’attribut *Default* défini dans **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Configurez les produits pour qu’ils aient des valeurs d’attribut *test*.

   * SKU : s00001, test : quatrième
   * SKU : s00002, test : troisième
   * SKU : s00003, test : deuxième
   * SKU : s00004, test : premier
   * SKU : s00005, test : quatrième
   * SKU : s00006, test : troisième

1. Réindexez et effacez le cache.
1. Positionnez-vous sur la catégorie de la vitrine.
1. Tri par l’attribut *test*.

<u>Résultats attendus</u> :

Les produits sont triés par l’attribut *test* .

<u>Résultats réels</u> :

Les produits ne sont pas triés par l’attribut *test* .

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
