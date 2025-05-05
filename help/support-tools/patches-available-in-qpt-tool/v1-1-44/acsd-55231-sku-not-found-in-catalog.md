---
title: "ACSD-55231 : erreur SKU introuvable lors de l’utilisation de la fonctionnalité de commande rapide"
description: Appliquez le correctif ACSD-55231 pour résoudre le problème Adobe Commerce en raison duquel vous obtenez *'Le SKU est introuvable dans le catalogue'* erreur lors de la tentative d’ajout d’un produit au panier à l’aide de la fonctionnalité de commande rapide.
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: 463c2c07-39ec-4b03-81f7-ec2f71f5af76
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-55231 : erreur SKU introuvable lors de l’utilisation de la fonctionnalité de commande rapide

Le correctif ACSD-55231 corrige le problème en raison duquel vous obtenez *’L’erreur SKU introuvable dans le catalogue&#39;* lors de la tentative d’ajout d’un produit au panier à l’aide de la fonctionnalité de commande rapide. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 est installé. L’ID de correctif est ACSD-55231. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Obtention de *&#39;le SKU introuvable dans le catalogue&#39;* lors de la recherche de produits à ajouter au panier à l’aide de la fonctionnalité de commande rapide.

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce avec les modules B2B.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** et définissez :
   * **[!UICONTROL Enable company]** : *Oui*
   * **[!UICONTROL Enable Shared Catalog]** : *Oui*
   * **[!UICONTROL Enable Quick Order]** : *Oui*
1. Enregistrez la configuration ci-dessus.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** et créez un catalogue partagé.
1. Accédez à **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** et créez un client :
   * Dans le champ de groupe, choisissez le catalogue partagé récemment créé et définissez *[!UICONTROL Allow remote shopping assistance]* sur *Oui*.
1. Générez un produit simple avec le SKU *p12*, associez-le à la catégorie *c1*, puis optez pour le catalogue partagé nouvellement créé dans la section [!UICONTROL Product in Shared Catalog].
1. Exécutez :

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. Actualisez la page d’administration.
1. Accédez à **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** et modifiez le client créé précédemment.
1. Cliquez sur **[!UICONTROL Login as customer]**.
1. Accédez à **[!UICONTROL Quick order]**.
1. Recherchez le SKU *p12* et cliquez sur le **[!UICONTROL Product Suggestion]**.
1. Ajoutez ce produit au panier et passez la commande.
1. Revenez à **[!UICONTROL Quick Order]**, recherchez à nouveau le SKU *p12*, puis cliquez sur **[!UICONTROL Product Suggestion]**.

<u>Résultats attendus</u> :

Vous pouvez ajouter le produit au panier à l’aide de la fonctionnalité de commande rapide.

<u>Résultats réels</u> :

Vous ne pouvez pas ajouter le produit au panier à l’aide de la fonctionnalité de commande rapide et obtenir *’L’erreur SKU est introuvable dans le catalogue&#39;* lors de la recherche du SKU du produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
