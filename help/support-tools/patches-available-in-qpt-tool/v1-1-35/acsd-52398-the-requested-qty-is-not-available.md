---
title: "ACSD-52398 : la quantité demandée n’est pas disponible lors de la tentative de mise à jour de la quantité de produit groupé"
description: Appliquez le correctif ACSD-52398 pour résoudre le problème Adobe Commerce en raison duquel la quantité demandée n’est pas disponible lors de la tentative de mise à jour de la quantité d’un produit regroupé dans le panier sur le storefront.
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 7b7f06ac-7913-4603-992a-a5620045d828
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-52398 : La quantité demandée n’est pas disponible lors de la tentative de mise à jour de la quantité de produit groupé.

Le correctif ACSD-52398 corrige le problème en raison duquel la quantité demandée n’est pas disponible lors de la tentative de mise à jour de la quantité d’un produit regroupé dans le panier sur le storefront. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.35 est installée. L’ID de correctif est ACSD-52398. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La quantité demandée n’est pas disponible lorsque vous tentez de mettre à jour la quantité d’un produit regroupé dans le panier sur le storefront.

<u>Étapes à reproduire</u>:

1. Créer deux produits simples avec une quantité *1* et *10*.
1. Créez un produit groupé à l’aide des produits simples.
1. Ajoutez le produit fourni au panier.
1. Modifiez le produit et essayez de mettre à jour la quantité sur *3* pour l’option où *10* sont disponibles.

<u>Résultats attendus</u>:

Il n’y a pas d’erreur. La qualité a été mise à jour avec succès, car il existe des *10* éléments en stock pour cette option.

<u>Résultats réels</u>:

L’erreur suivante est générée : *La quantité demandée n’est pas disponible.*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
