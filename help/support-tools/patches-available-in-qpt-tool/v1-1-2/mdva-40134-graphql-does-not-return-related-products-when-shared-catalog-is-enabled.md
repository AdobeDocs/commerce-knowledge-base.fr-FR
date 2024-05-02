---
title: 'MDVA-40134 : GraphQL ne renvoyant pas les produits associés lorsque le catalogue partagé est activé'
description: Le correctif MDVA-40134 corrige le problème en raison duquel GraphQL ne renvoie pas de produits associés lorsque le catalogue partagé est activé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-40134. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134 : GraphQL ne renvoie pas de produits associés lorsque le catalogue partagé est activé

Le correctif MDVA-40134 corrige le problème en raison duquel GraphQL ne renvoie pas de produits associés lorsque le catalogue partagé est activé. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.2 est installée. L’ID de correctif est MDVA-40134. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

GraphQL ne renvoie pas les produits associés lorsque le catalogue partagé est activé.

<u>Conditions préalables</u>:

Les modules B2B doivent être installés.
L’instance doit être propre avec uniquement les exemples de données.

<u>Étapes à reproduire</u>:

1. Accédez à **Magasins** > **Configuration** > **Général** > **Fonctionnalités B2B** et activez **Catalogue d’entreprise et partagé**.
1. Accédez à **Catalogue** > **Catalogue partagé** et ajoutez tous les produits au **Catalogue général**.
1. Utilisez les exemples de données et modifiez la balise Joust Duffle (SKU 24-MB01).
1. Sous **Produits associés**, ajoutez les deux sacs Duffle (ID 7 et 13).
1. Envoyer un **Post** request :

<pre>{ products(filter: {sku: {eq: "24-MB01"}}, sort: {name: ASC}) { items { related_products { uid name } } } } }</pre>

<u>Résultats attendus</u>:

Les produits associés s’affichent dans la réponse GraphQL.

<u>Résultats réels</u>:

Les utilisateurs reçoivent l’erreur suivante :

<pre>La valeur renvoyée de Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() doit être de type int, null return {"exception":"[objet] (GraphQL\\Error\\Error(code: 0) : la valeur renvoyée de Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() doit être de type int, null renvoyée. </pre>

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
