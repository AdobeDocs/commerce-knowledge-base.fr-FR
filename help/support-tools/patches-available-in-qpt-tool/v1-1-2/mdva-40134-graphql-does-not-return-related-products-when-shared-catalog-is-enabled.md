---
title: 'MDVA-40134 : GraphQL ne renvoyant pas les produits associés lorsque le catalogue partagé est activé'
description: Le correctif MDVA-40134 corrige le problème en raison duquel GraphQL ne renvoie pas de produits associés lorsque le catalogue partagé est activé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-40134. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134 : GraphQL ne renvoie pas de produits associés lorsque le catalogue partagé est activé

Le correctif MDVA-40134 corrige le problème en raison duquel GraphQL ne renvoie pas de produits associés lorsque le catalogue partagé est activé. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-40134. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

GraphQL ne renvoie pas les produits associés lorsque le catalogue partagé est activé.

<u>Conditions préalables</u> :

Les modules B2B doivent être installés.
L’instance doit être propre avec uniquement les exemples de données.

<u>Étapes à reproduire</u> :

1. Accédez à **Magasins** > **Configuration** > **Général** > **Fonctionnalités B2B** et activez **Société et catalogue partagé**.
1. Accédez à **Catalogue** > **Catalogue partagé** et ajoutez tous les produits au **catalogue général**.
1. Utilisez les exemples de données et modifiez la balise Joust Duffle (SKU 24-MB01).
1. Sous **Products** associés, ajoutez les deux sacs Duffle (ID 7 et 13).
1. Envoyez une requête **Post** :

<pre>&lbrace;
  products(filter: {sku: {eq: "24-MB01"}}, sort: {name: ASC}) &lbrace;
    items &lbrace;
      related_products &lbrace;
        uid
        name
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;</pre>

<u>Résultats attendus</u> :

Les produits associés s’affichent dans la réponse GraphQL.

<u>Résultats réels</u> :

Les utilisateurs reçoivent l’erreur suivante :

<pre>La valeur renvoyée de Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() doit être de type int, null return &lbrace;"exception":"[objet] (GraphQL\\Error\\Error(code: 0) : la valeur renvoyée de Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() doit être de type int, null renvoyée. </pre>

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
