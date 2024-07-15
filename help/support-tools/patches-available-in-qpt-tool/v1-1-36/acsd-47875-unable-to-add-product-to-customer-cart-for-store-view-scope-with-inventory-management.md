---
title: "ACSD-47875 : impossible d’ajouter un produit au panier pour la portée de la vue de magasin avec gestion de l’inventaire"
description: Appliquez le correctif ACSD-47875 pour résoudre le problème Adobe Commerce en raison duquel un produit ne peut pas être ajouté au panier d’un client par l’administrateur pour une portée de vue de magasin spécifique avec la gestion de l’inventaire.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: fa5ecd65-704f-49bd-b3cc-3d60ff7e1dce
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-47875 : impossible d’ajouter un produit au panier pour la portée de la vue de magasin avec gestion de l’inventaire

Le correctif ACSD-47875 corrige le problème lorsqu’un produit ne peut pas être ajouté au panier d’un client à partir de l’administrateur pour une portée de vue de magasin spécifique avec la gestion de l’inventaire. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.36 est installé. L’ID de correctif est ACSD-47875. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs administrateurs ne peuvent pas ajouter de produit au panier d’un client à l’aide de la fonction **[!UICONTROL Manage Shopping Cart]** de l’administrateur pour une plage d’affichage de magasin spécifique avec MSI installé.

<u>Conditions préalables</u> :

Les modules [!DNL Adobe Commerce Inventory Management (MSI)] sont installés et activés.

<u>Étapes à reproduire</u> :

1. Créez un site web, un magasin et une vue de magasin.
1. Créez une source supplémentaire autre que *Default*.
1. Créez un nouveau stock et affectez-le au nouveau site web et à la nouvelle source.
1. Créez un client pour le nouveau site web.
1. Attribuez un produit au nouveau site web uniquement ; annulez l’affectation à partir du site web par défaut.

   * Affectez la nouvelle source et définissez Qté *supérieure à 0* pour la nouvelle source et *0* pour la source par défaut.

1. Accédez à la page **[!UICONTROL Customer Edit]** de l’administrateur. Cliquez sur **[!UICONTROL Manage Shopping Cart]**.
1. Définissez la portée de la vue de magasin sur la nouvelle vue de magasin.
1. Accédez à la section **[!UICONTROL Products]** et recherchez le produit.
1. Sélectionnez le produit et cliquez sur **[!UICONTROL Add selections to my cart]**.

<u>Résultats attendus</u> :

Le produit est ajouté au panier.

<u>Résultats réels</u> :

* L&#39;erreur suivante est générée : *Le produit que vous essayez d&#39;ajouter n&#39;est pas disponible.*
* Le produit n’est pas ajouté au panier.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
