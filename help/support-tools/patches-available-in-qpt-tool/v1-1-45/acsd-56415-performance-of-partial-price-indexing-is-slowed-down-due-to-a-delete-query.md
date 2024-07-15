---
title: 'ACSD-56415 : les performances de [!UICONTROL Partial Price Indexing] ralenties en raison de la requête "DELETE"'
description: Appliquez le correctif ACSD-56415 pour résoudre le problème Adobe Commerce où les performances de [!UICONTROL Partial Price Indexing] sont ralenties en raison d’une requête "DELETE" lorsque la base de données contient un grand nombre de données de prix partielles à indexer.
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415 : les performances de [!UICONTROL Partial Price Indexing] sont ralenties en raison de la requête `DELETE`

Le correctif ACSD-56415 corrige le problème de ralentissement des performances de [!UICONTROL Partial Price Indexing] en raison d’une requête `DELETE` lorsque la base de données contient un index de données de prix partiel important. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 est installé. L’ID de correctif est ACSD-56023. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les performances de [!UICONTROL Partial Price Indexing] sont ralenties en raison d’une requête `DELETE` lorsque la base de données contient un grand nombre d’index de données de prix partiels.

<u>Étapes à reproduire</u> :

1. Créez *300000 produits* et *10 sites Web* à l&#39;aide du profil de performances volumineux.
1. Connectez-vous au panneau d’administration.
1. Créez *10 groupes de clients*.
1. Exécutez la requête ci-dessous pour ajouter des produits à la table `_cl` :

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. Exécutez la commande ci-dessous pour déclencher le processus d&#39;indexation de prix partiel :

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>Résultats attendus</u> :

Le DELETE de requête SQL `main_table` FROM `catalog_product_index_price` est exécuté rapidement.

<u>Résultats réels</u> :

Le DELETE de requête SQL `main_table` FROM `catalog_product_index_price` est exécuté très lentement.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
