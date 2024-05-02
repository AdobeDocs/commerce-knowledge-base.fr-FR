---
title: 'MDVA-28300 : problème de calcul du prix avec la règle de prix du catalogue dans GraphQL'
description: Le correctif MDVA-28300 corrige le problème où la demande GraphQL ne reflète pas les modifications de prix des règles de prix du catalogue. Ce correctif est disponible lorsque l’outil de correctifs de qualité (QPT) v.1.0.6 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.3.6.
exl-id: 86079d29-db69-4758-a159-aeed8e0ea21f
feature: Catalog Management, GraphQL, Customer Service, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# MDVA-28300 : problème de calcul du prix avec la règle de prix du catalogue dans GraphQL

>[!WARNING]
>
>Un nouveau correctif appelé MDVA-33975 corrige les problèmes de calcul des prix de GraphQL. Le MDVA-28300 est déprécié et il est recommandé d’appliquer le correctif MDVA-33975. Pour accéder à ce patch, reportez-vous à la section [MDVA-33975 : calculs des prix GraphQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

Le correctif MDVA-28300 corrige le problème où la demande GraphQL ne reflète pas les modifications de prix des règles de prix du catalogue. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.3.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce on-premise 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce on-premise et Adobe Commerce sur l’infrastructure cloud 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsqu’une règle de prix de catalogue est appliquée à un certain groupe de clients, les prix des articles dans le panier et le total des commandes ne sont pas correctement calculés dans GraphQL.

<u>Étapes à reproduire :</u>

1. Créez un compte client et remplacez le groupe de clients par Wholesale.
1. Créez une règle Catalogue dans **Marketing** > **Promotions** > **Règles de prix du catalogue** avec les paramètres suivants :
   * Groupes clients : WholesaleActions :
   * Appliquer : *Appliquer en tant que pourcentage de l’original*
   * Remise : *50*


1. Créez un produit avec price=100.
1. Connectez-vous au front-end à l’aide du compte client créé précédemment (si vous étiez déjà connecté, déconnectez-vous et reconnectez-vous).
1. Ajoutez le produit au panier. Le prix du produit est de 50 (prix normal 100) et Total de la commande : 55 (50 + 5 du coût de l&#39;expédition).
1. Exécutez l’appel API GraphQL décrit dans [Requête customerCart](https://devdocs.magento.com/guides/v2.3/graphql/queries/customer-cart.html) dans notre documentation destinée aux développeurs.

<u>Résultat attendu :</u>

L’API et le frontal ont le même total de commande avec la remise introduite par la règle de catalogue appliquée.

<u>Résultat réel :</u>

Le total de la commande n’applique pas la remise de règle de catalogue.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Application de correctifs à l’aide de l’outil Correctifs de qualité](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html).

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section Correctifs disponibles dans QPT .
