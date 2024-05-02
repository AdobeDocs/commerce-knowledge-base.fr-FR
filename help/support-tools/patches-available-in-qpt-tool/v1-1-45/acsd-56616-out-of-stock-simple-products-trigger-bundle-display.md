---
title: "ACSD-56616 : Affichage en première ligne de produits regroupés lors d’une simple pénurie de stock"
description: Appliquez le correctif ACSD-56616 pour résoudre le problème Adobe Commerce en raison duquel les produits regroupés apparaissent de manière inattendue sur le storefront lorsque tous les produits simples associés sont en rupture de stock.
feature: Products
role: Admin, Developer
exl-id: 6cf8e15d-38a5-42b6-aee7-67410b501404
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56616 : Affichage storefront de produits groupés lors d’une simple pénurie de stock.

Le correctif ACSD-56616 corrige le problème en raison duquel les produits regroupés apparaissent de manière inattendue sur le storefront lorsque tous les produits simples associés sont en rupture de stock. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.45 est installée. L’ID de correctif est ACSD-56616. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Affichage incorrect de la vitrine des produits groupés lors d’une simple pénurie de stock.

<u>Étapes à reproduire</u>:

1. Créez un site web/magasin/storefront.
1. Créez une source.
1. Créez un nouveau stock et affectez-le au site web nouvellement créé.
1. Configurez les indexeurs à mettre à jour selon le calendrier.
1. Générez deux produits simples, S1 (qty = 1) et S2 (qty = 1), et affectez-les au nouveau stock et au nouveau site web.
1. Créer *bundled1* produit et l’associer au nouveau site web, en le plaçant dans une catégorie *CAT*.
1. Définir deux options de liste déroulante requises et lier un produit simple *S1* à l’option 1 et *S2* à l’option 2.
1. Enregistrez les produits.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** et activez *Ajout de code de magasin à l’URL* = *Oui*.
1. Ouvrez le storefront et achetez le produit fourni.
1. Exécutez cron deux fois.
1. Revenez au *CAT* catégorie.

<u>Résultats attendus</u>:

La variable *bundle1* Le produit est en rupture de stock.

<u>Résultats réels</u>:

La variable *bundle1* produit visible avec prix = *0 $*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
