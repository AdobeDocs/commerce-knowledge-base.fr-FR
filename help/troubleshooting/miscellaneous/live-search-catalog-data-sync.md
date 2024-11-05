---
title: Catalogue de recherche en direct non synchronisé
description: Cet article fournit des solutions au problème Adobe Commerce en raison duquel les données de votre catalogue ne sont pas synchronisées correctement lors de l’utilisation de l’extension Live Search.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# Catalogue de recherche en direct non synchronisé

Cet article fournit des solutions au problème Adobe Commerce en raison duquel les données de votre catalogue ne sont pas synchronisées correctement lors de l’utilisation de l’extension Live Search.

## Produits et versions concernés

* Adobe Commerce 2.4.x avec l’extension Live Search installée

## Problème

Les données de votre catalogue ne sont pas synchronisées correctement ou un nouveau produit a été ajouté, mais n’apparaît pas dans les résultats de la recherche.

>[!NOTE]
>
>Les noms de table `catalog_data_exporter_products` et `catalog_data_exporter_product_attributes` sont désormais appelés `cde_products_feed` et `cde_product_attributes_feed` à partir de la version 4.2.1 de [!DNL Live Search]. Pour les marchands sur des versions antérieures à la version 4.2.1, recherchez les données des anciens noms de table, `catalog_data_exporter_products` et `catalog_data_exporter_product_attributes`.

<u>Étapes à reproduire</u>

1. Configurez et connectez Live Search pour votre instance Adobe Commerce comme décrit dans [Installer Live Search > Configurer les clés d’API](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#configure-api-keys) dans notre documentation utilisateur.
1. Après 30 minutes, vérifiez les données du catalogue exportées comme décrit dans [Installer la recherche en direct > Vérifier l’exportation](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#verify-export) dans notre documentation utilisateur.
1. Après 30 minutes, testez la connexion comme décrit dans [Installer la recherche en direct > Tester la connexion](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#test-connection) dans notre documentation utilisateur.

Ou

1. Ajoutez un nouveau produit au catalogue.
1. Essayez d’exécuter une requête de recherche en utilisant le nom du produit ou d’autres attributs pouvant faire l’objet d’une recherche après 15 à 20 minutes à compter de l’exécution de l’indexeur de Magento + cron pour synchroniser les données avec le service principal.

<u>Résultat attendu</u>

* Les données de catalogue exportées peuvent être vérifiées
* Connexion réussie
* Un nouveau produit apparaît dans les résultats de recherche.

<u>Résultat réel</u>

Le catalogue exporté ne peut pas être vérifié et/ou la connexion n’est pas établie car la clé d’API a changé.

## Solution

Vous pouvez effectuer plusieurs opérations pour résoudre les problèmes de synchronisation du catalogue.

### Attendez que les modifications soient appliquées.

Une fois que vous avez configuré et connecté, il peut s’écouler plus de 30 minutes avant que l’index dans ES (Elasticsearch) ne soit créé et que les résultats de la recherche soient renvoyés. Les mises à jour ponctuelles suivantes du produit doivent être indexées dans les minutes qui suivent.

### Synchronisation des données de produit pour un SKU spécifique

Si les données de votre produit ne sont pas synchronisées correctement pour un SKU spécifique, procédez comme suit :

1. Utilisez la requête [!DNL SQL] suivante et vérifiez que vous disposez des données attendues dans la colonne `feed_data`. Notez également l’horodatage `modified_at`.

   ```sql
   select * from cde_products_feed where sku = '<your_sku>' and store_view_code = '<your_ store_view_code>';
   ```

1. Si vous ne voyez pas les données correctes, essayez de réindexer à l’aide de la commande suivante et réexécutez la requête [!DNL SQL] à l’étape 1 pour vérifier les données :

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. Si vous ne voyez toujours pas les données correctes, [créez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Vérification de l’horodatage de la dernière exportation de produit

1. Si vous voyez les données correctes dans `cde_products_feed`, utilisez la requête [!DNL SQL] suivante pour vérifier l’horodatage de la dernière exportation. Elle doit être postérieure à l’horodatage `modified_at` :

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Si l’horodatage est plus ancien, vous pouvez attendre la prochaine exécution cron ou la déclencher vous-même à l’aide de la commande suivante :

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Patientez pendant `<>` (temps pour les mises à jour incrémentielles). Si vos données ne s’affichent toujours pas, [créez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Code d’attribut spécifique à la synchronisation

Si les données d’attribut de produit ne sont pas synchronisées correctement pour un code d’attribut spécifique, procédez comme suit :

1. Utilisez la requête [!DNL SQL] suivante et vérifiez que vous disposez des données attendues dans la colonne `feed_data`. Notez également l’horodatage `modified_at`.

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Si vous ne voyez pas les données correctes, utilisez la commande suivante pour réindexer, puis réexécutez la requête [!DNL SQL] à l’étape 1 pour vérifier les données.

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. Si vous ne voyez toujours pas les données correctes, [créez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Vérification de l’horodatage de la dernière exportation d’attributs de produit

Si vous voyez les données correctes dans `cde_product_attributes_feed` :

1. Utilisez la requête [!DNL SQL] suivante pour vérifier l’horodatage de la dernière exportation. Elle doit être postérieure à l’horodatage `modified_at`.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Si l’horodatage est plus ancien, vous pouvez attendre la prochaine exécution cron ou la déclencher vous-même à l’aide de la commande suivante :

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Patientez 15 à 20 minutes (durée des mises à jour incrémentielles). Si vos données ne s’affichent toujours pas, [créez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Synchronisation après modification de la configuration de l’API

(Problème connu) Si vous avez modifié la configuration de votre API, qui entraîne un changement de votre ID d’espace de données et que vous constatez que vos modifications de catalogue ne sont plus synchronisées, exécutez les commandes suivantes :

```bash
bin/magento saas:resync --feed products
bin/magento saas:resync --feed productattributes
```

## Lecture connexe

* [Recherche en direct intégrée](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html) dans notre documentation utilisateur
* [Consultez les journaux et résolvez les problèmes d’exportation et de synchronisation des données SaaS Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) dans le guide d’exportation des données SaaS Adobe Commerce
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
