---
title: "ACSD-51683 : l’option personnalisable ne peut pas être ajoutée au panier à l’aide de GraphQL"
description: Appliquez le correctif ACSD-51683 pour résoudre le problème Adobe Commerce en raison duquel l’option personnalisable ne peut pas être ajoutée au panier à l’aide de GraphQL.
feature: GraphQL
role: Admin
exl-id: 4de0d8b7-714e-4bbf-8a0d-bb6e0c3aae55
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51683 : l’option personnalisable ne peut pas être ajoutée au panier à l’aide de GraphQL

Le correctif ACSD-51683 corrige le problème en raison duquel l’option personnalisable ne peut pas être ajoutée au panier à l’aide de GraphQL. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 est installé. L’ID de correctif est ACSD-51683. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’option personnalisable ne peut pas être ajoutée au panier à l’aide de GraphQL.

<u>Étapes à reproduire</u> :

1. Créez un produit simple avec une option personnalisable **Champ de texte** .
1. [Ajoutez au panier](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) le produit créé avec l’option personnalisable requise via GraphQL.
1. Envoyez la demande GraphQL [cart](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) pour vérifier le produit et ses détails dans le panier.

<u>Résultats attendus</u>

La section `Customizable_options` de la réponse GraphQL contient les données fournies lors de l’ajout du produit au panier.

<u>Résultats réels</u>

La section `Customizable_options` de la réponse GraphQL est vide.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
