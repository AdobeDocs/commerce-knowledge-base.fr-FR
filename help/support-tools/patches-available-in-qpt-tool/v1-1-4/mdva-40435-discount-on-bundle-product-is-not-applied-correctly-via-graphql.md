---
title: "MDVA-40435 : la remise sur le produit groupé n’est pas appliquée correctement via GraphQL"
description: Le correctif MDVA-40435 résout le problème en raison duquel la remise sur un produit groupé n’est pas correctement appliquée via GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 est installé. L’ID de correctif est MDVA-40435. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 939ba940-35b5-4ab0-81fe-38981246e389
feature: GraphQL, Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-40435 : La remise sur le produit groupé n’est pas appliquée correctement via GraphQL

Le correctif MDVA-40435 résout le problème en raison duquel la remise sur un produit groupé n’est pas correctement appliquée via GraphQL. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 est installé. L’ID de correctif est MDVA-40435. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La remise sur un produit groupé n’est pas appliquée correctement via GraphQL.

<u>Étapes à reproduire</u> :

1. Créez une règle de prix de panier avec un code de bon pour une remise fixe de 5 €.
1. Créez un panier vide via GraphQL.
1. Ajoutez un produit fourni au panier via GraphQL.
1. Appliquez le code coupon sur le montant fixe (5$) via GraphQL.
1. Obtenez les informations du panier via GraphQL.

<u>Résultats attendus</u> :

&quot;remises&quot; est de 5 $.

<u>Résultats réels</u> :

&quot;remises&quot; est NULL.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
