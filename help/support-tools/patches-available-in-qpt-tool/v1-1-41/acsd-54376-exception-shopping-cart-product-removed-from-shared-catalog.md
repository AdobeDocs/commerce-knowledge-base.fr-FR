---
title: 'ACSD-54376 : exception dans le panier lorsque le produit est supprimé de [!UICONTROL shared catalog]'
description: Appliquez le correctif ACSD-54376 pour résoudre le problème d’Adobe Commerce lorsqu’une exception se produit dans le panier lorsqu’un produit est supprimé du [!UICONTROL shared catalog] après avoir été ajouté au panier.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: a1e5c084-532f-49e8-ab87-6674b44218e8
source-git-commit: 1cc565d5888e5a380c04879d9aced2c19e92c2e5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54376 : exception dans le panier lorsque le produit est supprimé de [!UICONTROL shared catalog]

Le correctif ACSD-54376 corrige le problème lorsqu’une exception se produit dans le panier lorsqu’un produit est supprimé de la variable [!UICONTROL shared catalog] après avoir été ajouté au panier. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.41 est installée. L’ID de correctif est ACSD-54376. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une exception se produit dans le panier lorsqu’un produit est supprimé de la variable [!UICONTROL shared catalog] après avoir été ajouté au panier.

<u>Étapes à reproduire</u>:

1. Installez Adobe Commerce avec B2B.
1. Activer [!UICONTROL shared catalog].
1. Créez un produit et affectez-le à la valeur par défaut. [!UICONTROL shared catalog].
1. Ajoutez un produit au panier à partir du storefront.
1. Supprimez le produit du [!UICONTROL shared catalog].
1. Accédez à la page de passage en caisse à l’aide de la liste déroulante des mini-paniers.

<u>Résultats attendus</u>:

Les exceptions sont gérées et ne s’affichent pas.

<u>Résultats réels</u>:

Une exception non gérée s’affiche sur la page de passage en caisse.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
