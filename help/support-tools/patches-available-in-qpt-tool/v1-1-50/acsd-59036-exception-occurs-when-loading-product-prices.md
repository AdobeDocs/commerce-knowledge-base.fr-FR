---
title: "ACSD-59036 : une exception se produit lors du chargement des prix des produits pour lesquels les limites inférieure et supérieure sont définies sur 0 $"
description: Appliquez le correctif ACSD-59036 pour résoudre le problème d’Adobe Commerce en raison duquel une exception se produit lors du chargement des prix des produits avec des limites inférieure et supérieure définies sur *$0*.
feature: Categories, Products, Storefront, Search
role: Admin, Developer
source-git-commit: d711fb8ff8876a4a514daade6d7df4d7cf7e3593
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# ACSD-59036 : une exception se produit lors du chargement des prix des produits avec des limites inférieure et supérieure définies sur *$0*

Le correctif ACSD-59036 corrige le problème lorsqu’une exception se produit lors du chargement des prix des produits avec des limites inférieure et supérieure définies sur *$0*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 est installé. L’ID de correctif est ACSD-59036. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une exception se produit lors du chargement des prix des produits avec des limites inférieure et supérieure définies sur *$0*.

Le problème se produit car l’algorithme ne prend pas en compte les valeurs NULL lors du chargement de la requête avec des plages de prix. Pour corriger ce problème, nous pouvons vérifier si les plages inférieures et supérieures sont NULL et, si elles le sont, attribuer une valeur *0* pour les deux limites. Cela devrait empêcher le lancement d’erreurs.

<u>Étapes à reproduire</u> :

1. Créez des produits *13* simples.
1. Affectez tous les produits *13* à une catégorie.
1. Définissez le prix d’un produit sur *$1322.94*.
1. Définissez le prix de tous les autres produits sur *$0*.
1. Configurez [!DNL OpenSearch] comme moteur de recherche.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** et définissez le nombre **[!UICONTROL PLP]** sur *16*.
1. Définissez **[!UICONTROL Price Navigation Step Calculation]** sur *Automatique (égalisez le nombre de produits)*.
1. Exécutez la réindexation complète.
1. Ouvrez la page *[!UICONTROL Category]* .

<u>Résultats attendus</u> :

La page *[!UICONTROL Category]* affiche tous les produits.

<u>Résultats réels</u> :

Une erreur se produit :

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
