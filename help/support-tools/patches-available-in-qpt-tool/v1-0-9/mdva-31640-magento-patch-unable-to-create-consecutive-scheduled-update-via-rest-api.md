---
title: '''Correctif MDVA-31640 : impossible de créer une mise à jour planifiée consécutive via l''API REST'''
description: Le correctif MDVA-31640 corrige le problème lorsqu’une nouvelle mise à jour planifiée pour le prix spécial ne peut pas être créée pour plusieurs magasins à l’aide de l’API REST, si la date de début de la mise à jour correspond à la date de fin de la mise à jour existante précédemment. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 8d91db3d-7c94-4757-8087-4cf53cad81e7
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Correctif MDVA-31640 : impossible de créer une mise à jour planifiée consécutive via l&#39;API REST.

Le correctif MDVA-31640 corrige le problème lorsqu’une nouvelle mise à jour planifiée pour le prix spécial ne peut pas être créée pour plusieurs magasins à l’aide de l’API REST, si la date de début de la mise à jour correspond à la date de fin de la mise à jour existante précédemment. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif a été créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.1 - 2.3.5-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Correction d’un problème en raison duquel une nouvelle mise à jour planifiée pour le prix spécial ne pouvait pas être créée pour plusieurs magasins utilisant l’API REST, si la date de début de la mise à jour correspond à la date de fin de la mise à jour existante précédemment.

<u>Étapes à reproduire</u> :

1. Configurez un autre affichage de site web, de magasin et de magasin.
1. Créez deux produits simples : &quot;product1&quot; et &quot;product2&quot;.
1. Affectez product1 à un site web et product2 aux deux sites web.
1. Créez une mise à jour planifiée pour le prix spécial du produit1 sur la vue de magasin pour le magasin avec l’ID 1. Utilisez la requête d’API REST `POST` vers `rest/V1/products/special-price` avec la charge utile suivante :
   `{        "prices": [            {                "price": 15,                "store_id": 1,                "sku": "product1",                "price_from": "2021-11-15 04:00:00",                "price_to": "2021-11-15 04:10:00"            }        ]    }`
1. Créez une mise à jour planifiée pour le prix spécial du produit2 sur les deux vues de magasin pour les magasins avec l’ID 1 et 2 à l’aide de la requête `POST` de l’API REST à `rest/V1/products/special-price` avec la charge utile suivante (la date `price_from` est identique à la date `price_to` de la requête précédente) :
   `{        "prices": [            {                "price": 14,                "store_id": 1,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            },            {                "price": 13,                "store_id": 2,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            }        ]    }`

<u>Résultats attendus</u> :

La mise à jour planifiée avec le changement de prix spécial est créée sur les deux vues de magasin.

<u>Résultats réels</u> :

Adobe Commerce renvoie une erreur. La mise à jour planifiée n’est pas créée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
