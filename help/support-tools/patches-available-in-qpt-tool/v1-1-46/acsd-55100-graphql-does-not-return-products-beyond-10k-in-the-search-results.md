---
title: "ACSD-55100: [!DNL GraphQL] ne renvoie pas de produits au-delà de 10K dans les résultats de recherche"
description: Appliquez le correctif ACSD-55100 pour résoudre le problème Adobe Commerce en raison duquel GraphQL ne renvoie pas de produits au-delà de *10k* dans les résultats de recherche.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100 : [!DNL GraphQL] ne renvoie pas de produits au-delà de 10K dans les résultats de recherche

Le correctif ACSD-55100 corrige le problème où [!DNL GraphQL] ne renvoie pas de produits au-delà de *10k* dans les résultats de recherche. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 est installé. L’ID de correctif est ACSD-55100. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL GraphQL] ne renvoie pas de produits au-delà de *10k* dans les résultats de recherche.

<u>Conditions préalables</u> :

Dans le cas de **[!DNL OpenSearch]**, vérifiez que vous utilisez la dernière version disponible.

Pour résoudre le problème signalé, la fonctionnalité Point dans le temps est introduite, disponible après **[!DNL OpenSearch]** 2.5.0 et qui nécessite la version 2.2 du package `opensearch-project/opensearch-php`.

Cependant, il existe un conflit avec `magento/magento-cloud-metapackage`, qui spécifie une dépendance sur le package `opensearch-project/opensearch-php` qui doit être inférieure à la version 2.0.1.


Cette dépendance empêche la mise à jour du package [opensearch-project/opensearch-php] vers la dernière version 2.2.

Par conséquent, le système rencontre l’erreur suivante et renvoie des résultats nuls pour les produits supérieurs à *10,000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

La dépendance existante rend difficile l’ajout direct d’une version au fichier `composer.json` et la mise à jour du package `opensearch-project/opensearch-php` vers la version 2.2.

Pour résoudre ce problème, insérez la ligne suivante dans votre fichier principal `composer.json` sous le bloc require (Obligatoire). Ensuite, redéployez pour mettre à jour le package problématique vers la dernière version.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Étapes à reproduire</u> :

1. Générez le catalogue avec les produits *15k*.
1. Envoyez le [!DNL GraphQL] :

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>Résultats attendus</u> :

Total_count = *15k*
Vous devriez être en mesure d’afficher tous les produits.

<u>Résultats réels</u> :

Total_count = *10k*
Vous ne pouvez pas obtenir d’autres produits à afficher après le lot *10k*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
