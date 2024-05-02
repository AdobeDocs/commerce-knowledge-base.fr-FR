---
title: 'Correctif MDVA-33975 : calculs des prix GraphQL'
description: Le correctif MDVA-33975 corrige les problèmes de calcul des prix de GraphQL. Ces problèmes incluent :'
exl-id: a8266334-72cb-4b50-9ff5-9a977d762e5c
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Correctif MDVA-33975 : calculs des prix GraphQL

Le correctif MDVA-33975 corrige les problèmes de calcul des prix de GraphQL. Ces problèmes sont les suivants :

* Lorsqu’une règle de prix de catalogue est appliquée à un certain groupe de clients, les prix des articles dans le panier et le total de la commande ne sont pas correctement calculés dans GraphQL.
* Les règles de prix du catalogue ne sont pas incluses dans `CartItemPrices` dans l’API.
* Le prix du groupe de clients pour le client général n’est pas ajouté dans la réponse de requête de produit GraphQL.
* Recalculer les totaux des guillemets avant de donner une réponse sur les prix entraîne la perte des règles appliquées.
* La remise sur le montant de la livraison n’a pas été récupérée à la dernière étape de facturation et le total général n’a pas été affiché correctement.
* La remise n’est pas appliquée dans GraphQL lorsque le segment client est utilisé dans la condition de la règle de prix du panier.

Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.14 est installé.

## Produits et versions concernés

* Le correctif a été conçu pour Adobe Commerce sur site 2.4.1.
* Le correctif est également compatible avec les versions d’Adobe Commerce suivantes : Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.4 à 2.4.1.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants, en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
