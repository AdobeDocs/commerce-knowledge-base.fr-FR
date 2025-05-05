---
title: 'ACSD-53309 : Application fiscale incomplète pour les options personnalisables et [!UICONTROL Regular Price]'
description: Appliquez le correctif ACSD-53309 pour résoudre le problème Adobe Commerce où la taxe n'est pas entièrement appliquée dans l'étiquette '[!UICONTROL Regular Price]' lorsqu'une option personnalisable est sélectionnée.
feature: Taxes, Shipping/Delivery
role: Admin, Developer
exl-id: de9b151e-6f92-4231-9e9f-4818c2961782
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-53309 : Application fiscale incomplète pour les options personnalisables et étiquette &#39;[!UICONTROL Regular Price]&#39;

Le correctif ACSD-53309 corrige le problème en raison duquel la taxe n’est pas entièrement appliquée dans l’étiquette &quot;[!UICONTROL Regular Price]&quot; lorsqu’une option personnalisable est sélectionnée. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 est installé. L’ID de correctif est ACSD-53309. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La taxe n’est pas entièrement reflétée dans l’étiquette &quot;[!UICONTROL Regular Price]&quot; lorsqu’une option personnalisable est sélectionnée.

<u>Étapes à reproduire</u> :

1. Connectez-vous au panneau Admin.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** pour configurer les paramètres de taxe.

   * [!UICONTROL Tax Classes] :

      * [!UICONTROL Tax Class for Shipping] = [!UICONTROL Taxable Goods]
      * [!UICONTROL Tax Class for Gift Options] = [!UICONTROL Taxable Goods]

   * [!UICONTROL Calculation Settings] :

      * [!UICONTROL Catalog Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Shipping Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Apply Discount On Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Default Tax Destination Calculation] :

      * [!UICONTROL Default Post Code] = *

   * [!UICONTROL Price Display Settings] :

      * [!UICONTROL Display Product Prices In Catalog] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Shopping Cart Display Settings] :

      * [!UICONTROL Display Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Subtotal] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Amount] = [!UICONTROL Including Tax]

1. Définissez **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** > **[!UICONTROL Country]** = *Royaume-Uni*.

1. Créez les *[!UICONTROL Tax Rate]* et *[!UICONTROL Tax Rules]* suivants :

   * [!UICONTROL Country] = États-Unis
   * [!UICONTROL Zip Code] = *
   * [!UICONTROL State] = *
   * [!UICONTROL Rate] = 20 %
1. Créez un produit simple et définissez les éléments suivants :
   * [!UICONTROL Price = 110]
   * [!UICONTROL Special Price = 100]
   * Dans la liste déroulante, définissez le type sur l’option personnalisée avec le prix défini sur 15 %.
1. Accédez à la page produit pour l’article simple créé sur le storefront.
1. Choisissez l&#39;option personnalisée créée, *15%*.

<u>Résultats attendus</u> :

* La taxe de 20 % est appliquée sur l’option personnalisée sélectionnée.
* &#39;[!UICONTROL Regular Price]&#39; = 151.80.

<u>Résultats réels</u> :

* La taxe de 20 % n’est pas appliquée à l’option personnalisée sélectionnée.
* &#39;[!UICONTROL Regular Price]&#39; = 148.50.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
