---
title: "ACSD-56546 : les produits configurables et groupés s’affichent en rupture de stock sur le storefront"
description: Appliquez le correctif ACSD-56546 pour résoudre le problème Adobe Commerce en raison duquel les produits configurables et groupés s’affichent en rupture de stock sur le storefront lorsque le *[!UICONTROL Display Out of Stock Products]* l’option de configuration est désactivée.
feature: Storefront, Products
role: Admin, Developer
exl-id: 488e2c69-442f-45e1-aa8f-71d9c0a93950
source-git-commit: 031d5cad6727bac61c88f21fa7c84e0d2a6df331
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-56546 : les produits configurables et groupés s’affichent en rupture de stock sur le storefront.

Le correctif ACSD-56546 corrige le problème en raison duquel les produits configurables et groupés s’affichent en rupture de stock sur le storefront. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.48 est installée. L’ID de correctif est ACSD-56546. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits configurables et groupés s’affichent en rupture de stock sur le storefront lorsque *[!UICONTROL Display Out of Stock Products]* est désactivée.

<u>Étapes à reproduire</u>:

1. Définissez la variable **[!UICONTROL Display Out of Stock Products]** option à *Non*.
1. Créez un site web, un magasin et un storeview.
1. Créez une source et un stock, puis attribuez-le au deuxième site web.
1. Créez un *produit configurable* avec deux produits enfants. Affectez les produits enfants à la fois aux sources et aux deux sites web.
1. Mettez à jour le premier produit enfant pour avoir *qty=0* dans les deux sources.
1. Mettez à jour le deuxième produit enfant et désactivez-le sur le deuxième site web.
1. Effectuez une réindexation complète.
1. Vérifiez la catégorie contenant le produit configurable sur le deuxième site web.

<u>Résultats attendus</u>:

Les produits configurables en rupture de stock ne sont pas visibles sur le storefront.

<u>Résultats réels</u>:

Les produits configurables en rupture de stock sont visibles sur le storefront, même lorsque la variable *[!UICONTROL Display Out of Stock Products]* est désactivée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
