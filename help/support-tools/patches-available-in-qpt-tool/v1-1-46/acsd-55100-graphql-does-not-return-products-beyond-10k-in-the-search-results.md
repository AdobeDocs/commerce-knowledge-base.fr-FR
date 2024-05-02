---
title: "ACSD-55100 : [!DNL GraphQL] ne renvoie pas de produits au-delà de 10 000 dans les résultats de recherche."
description: Appliquez le correctif ACSD-55100 pour résoudre le problème Adobe Commerce en raison duquel GraphQL ne renvoie pas de produits au-delà de *10k* dans les résultats de recherche.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100 : [!DNL GraphQL] ne renvoie pas de produits au-delà de 10 000 dans les résultats de recherche

Le correctif ACSD-55100 corrige le problème où [!DNL GraphQL] ne renvoie pas de produits au-delà de *10k* dans les résultats de la recherche. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.46 est installée. L’ID de correctif est ACSD-55100. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL GraphQL] ne renvoie pas de produits au-delà de *10k* dans les résultats de la recherche.

<u>Conditions préalables</u>:

En cas de **[!DNL OpenSearch]**, vérifiez que vous utilisez la dernière version disponible.

Pour résoudre le problème signalé, la fonctionnalité Point dans le temps est introduite, disponible après **[!DNL OpenSearch]** 2.5.0 et requiert la version 2.2 de la `opensearch-project/opensearch-php` module.

Cependant, il existe un conflit avec la variable `magento/magento-cloud-metapackage`, qui spécifie une dépendance sur la variable `opensearch-project/opensearch-php` module qui doit être inférieur à la version 2.0.1.


Cette dépendance empêche la mise à jour de la variable [opensearch-project/opensearch-php] vers la dernière version 2.2.

Par conséquent, le système rencontre l’erreur suivante et renvoie des résultats nuls pour les produits qui dépassent *10 000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

La dépendance existante complique l’ajout direct d’une version à la variable `composer.json` et mettre à jour le fichier `opensearch-project/opensearch-php` vers la version 2.2.

Pour résoudre ce problème, insérez la ligne suivante dans votre principale `composer.json` sous le bloc require . Ensuite, redéployez pour mettre à jour le package problématique vers la dernière version.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Étapes à reproduire</u>:

1. Générer le catalogue avec *15k* produits.
1. Envoyez la variable [!DNL GraphQL]:

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

<u>Résultats attendus</u>:

Total_count = *15k*
Vous devriez être en mesure d’afficher tous les produits.

<u>Résultats réels</u>:

Total_count = *10k*
Vous ne pouvez plus afficher de produits après la *10k* par lot.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
