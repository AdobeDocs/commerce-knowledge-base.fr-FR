---
title: "ACSD-44938 : L’ID de TVA ne peut pas être appliqué dans une demande GraphQL pour un utilisateur invité"
description: Le correctif ACSD-44938 corrige le problème qui empêchait l’application de l’identifiant TVA dans une requête GraphQL pour un utilisateur invité. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 est installé. L’ID de correctif est ACSD-44938. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: 18b3dfa5-b666-491e-a067-526a53294f39
feature: Admin Workspace, GraphQL
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-44938 : L’ID de TVA ne peut pas être appliqué dans la requête GraphQL pour un utilisateur invité.

Le correctif ACSD-44938 corrige le problème qui empêchait l’application de l’identifiant TVA dans une requête GraphQL pour un utilisateur invité. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.18 est installé. L’ID de correctif est ACSD-44938. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut TVA_ID ne peut pas être appliqué dans une requête GraphQL pour un utilisateur invité.

<u>Étapes à reproduire</u> :

1. Suivez les étapes mentionnées dans le [tutoriel GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/checkout-shopping-cart.html) de notre documentation destinée aux développeurs pour créer un panier d’invité.
1. Essayez d’appliquer l’attribut TVA_ID pour l’utilisateur invité à l’aide de GraphQL.

<u>Résultats attendus</u> :

L’attribut TVA_ID peut être appliqué de la même manière que pour un client enregistré. Voir l’article [mutation createCustomerAddress](https://developer.adobe.com/commerce/webapi/graphql/mutations/create-customer-address.html) dans notre documentation destinée aux développeurs.

<u>Résultats réels</u> :

L’attribut TVA_ID ne peut pas être appliqué à un utilisateur invité utilisant GraphQL.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
