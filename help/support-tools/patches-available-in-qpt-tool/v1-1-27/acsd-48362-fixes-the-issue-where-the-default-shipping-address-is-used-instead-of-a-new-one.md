---
title: 'ACSD-48362 : l’adresse de livraison par défaut est utilisée à la place d’une nouvelle.'
description: Appliquez le correctif ACSD-48362 pour résoudre le problème Adobe Commerce en raison duquel l’adresse de livraison par défaut est utilisée à la place d’une nouvelle adresse lors du placement d’une commande à l’aide d’un guillemet négociable.
exl-id: 52f518b6-6f73-42cc-ac1b-c893cd5007fa
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-48362 : l’adresse de livraison par défaut est utilisée au lieu d’une nouvelle.

Le correctif ACSD-48362 corrige le problème en raison duquel l’adresse de livraison par défaut est utilisée à la place de l’adresse nouvellement ajoutée lors du placement d’une commande à l’aide d’un guillemet négociable. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 est installé. L’ID de correctif est ACSD-48362. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’adresse de livraison par défaut est utilisée à la place de l’adresse de livraison nouvellement ajoutée lors du placement d’une commande à l’aide d’un guillemet négociable.

<u>Étapes à reproduire</u> :

1. Activez les guillemets B2B en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. Connectez-vous en tant qu’utilisateur d’entreprise.
1. Ajoutez un produit au panier.
1. Accédez à la page du panier et demandez un devis.
1. Accédez à la page **[!UICONTROL My Quotes]** du client et sélectionnez le guillemet qui vient d’être créé.
1. Accédez à la section **[!UICONTROL Shipping Information]** de la page de devis du client.
   * Cliquez sur **[!UICONTROL Add New Address]**, remplissez le formulaire et enregistrez l&#39;adresse (ne sélectionnez pas **[!UICONTROL Use as my default billing address]** ou **[!UICONTROL Use as my default shipping address]**).
1. Cliquez sur **[!UICONTROL Send for Review]** sur la page de devis du client.
1. Accédez à l’administrateur Adobe Commerce en tant qu’utilisateur administrateur, ouvrez le guillemet qui vient d’être créé, puis cliquez sur **[!UICONTROL Send]**.
1. Accédez maintenant à la page de devis du client, actualisez la page, puis cliquez sur **[!UICONTROL Proceed to Checkout]**.
1. Sur la page de passage en caisse, les données indiquent l’adresse de livraison par défaut, même si la nouvelle adresse de livraison est sélectionnée.
1. Cliquez sur **[!UICONTROL Continue]** et passez la commande.

<u>Résultats attendus</u> :

La commande doit utiliser la nouvelle adresse sans resélectionner l’adresse de livraison par défaut sur la page de passage en caisse.

<u>Résultats réels</u> :

La commande est placée avec l’adresse de livraison par défaut.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure. 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
