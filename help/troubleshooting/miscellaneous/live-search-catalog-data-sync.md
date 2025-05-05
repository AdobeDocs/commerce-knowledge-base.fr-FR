---
title: Catalogue de recherches en direct non synchronisé
description: Cet article fournit des solutions au problème d’Adobe Commerce en raison duquel les données de votre catalogue ne sont pas correctement synchronisées lors de l’utilisation de l’extension Live Search.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: fec99ebd6b03f2dc1b70c0ea388935dc5e60ad57
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---

# Catalogue de recherches en direct non synchronisé

Cet article fournit des solutions au problème d’Adobe Commerce en raison duquel les données de votre catalogue ne sont pas correctement synchronisées lors de l’utilisation de l’extension Live Search.

## Produits et versions concernés

* Adobe Commerce 2.4.x avec extension Live Search installée

## Problème

Les données de votre catalogue ne sont pas synchronisées correctement ou un nouveau produit a été ajouté mais n’apparaît pas dans les résultats de recherche. Il se peut également que l’erreur suivante s’affiche dans le `var/log/exception.log` :

`Magento_LiveSearch: An error occurred in search backend. {"result":{"errors":[{"message":"Exception while fetching data (/productSearch) : No index was found for this request"}]}}`

>[!NOTE]
>
>Les noms de table `catalog_data_exporter_products` et `catalog_data_exporter_product_attributes` sont désormais appelés `cde_products_feed` et `cde_product_attributes_feed` à partir de [!DNL Live Search] version 4.2.1. Pour les commerçants utilisant des versions antérieures à la version 4.2.1, recherchez les données dans les anciens noms de table, `catalog_data_exporter_products` et `catalog_data_exporter_product_attributes`.

<u>Procédure à suivre</u>

1. Configurez et connectez Live Search à votre instance Adobe Commerce, comme décrit dans [Installation de Live Search > Configuration des clés d’API](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=fr#configure-api-keys) dans notre documentation utilisateur.
1. Au bout de 30 minutes, vérifiez les données de catalogue exportées, comme décrit dans [Installer Live Search > Vérifier l’exportation](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=fr#verify-export) dans notre documentation utilisateur.
1. Au bout de 30 minutes, testez la connexion comme décrit dans [Installer Live Search > Tester la connexion](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=fr#test-connection) dans notre documentation utilisateur.

Ou

1. Ajoutez un nouveau produit au catalogue.
1. Essayez d’exécuter une requête de recherche à l’aide du nom du produit ou d’autres attributs pouvant faire l’objet de recherches après 15 à 20 minutes à compter de l’exécution de l’indexeur Magento + cron pour synchroniser les données avec le service principal.

<u>Résultat attendu</u>

* Les données de catalogue exportées peuvent être vérifiées.
* Connexion réussie
* Un nouveau produit apparaît dans les résultats de la recherche.

<u>Résultat réel</u>

Le catalogue exporté ne peut pas être vérifié et/ou la connexion n’est pas établie car la clé API a changé.

## Solution

Vous pouvez prendre plusieurs mesures pour essayer de résoudre les problèmes de synchronisation des catalogues.

### Attendre que les modifications soient appliquées

Une fois que vous avez configuré et connecté, la création de l’index dans ES (Elasticsearch) et le renvoi des résultats de recherche peuvent prendre plus de 30 minutes. Les mises à jour de produit ponctuelles suivantes doivent être indexées dans les minutes qui suivent.

### Synchroniser les données de produit pour un SKU spécifique

Si les données de votre produit ne sont pas correctement synchronisées pour un SKU spécifique, procédez comme suit :

1. Utilisez la requête [!DNL SQL] suivante et vérifiez que vous disposez des données attendues dans la colonne `feed_data`. Notez également l’horodatage `modified_at`.

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '<your_sku>' AND json_extract(feed_data, '$.storeViewCode') = '<your_ store_view_code>';
   ```

   Par exemple :

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '24-MB04' AND json_extract(feed_data, '$.storeViewCode') = 'default';
   ```

1. Si vous ne voyez pas les données correctes, essayez de réindexer à l’aide de la commande suivante et exécutez à nouveau la requête [!DNL SQL] à l’étape 1 pour vérifier les données :

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. Si les données correctes ne s’affichent toujours pas, [créez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Vérifier l’horodatage de la dernière exportation de produit

1. Si les données correctes s’affichent dans `cde_products_feed`, utilisez la requête [!DNL SQL] suivante pour vérifier l’horodatage de la dernière exportation. Elle doit être postérieure à l’horodatage `modified_at` :

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Si l’horodatage est plus ancien, vous pouvez attendre la prochaine exécution cron ou le déclencher vous-même à l’aide de la commande suivante :

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Temps d&#39;attente de `<>` (temps des mises à jour incrémentielles). Si vos données ne s’affichent toujours pas, [créez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Synchroniser le code d’attribut spécifique

Si les données d’attributs de produit ne sont pas correctement synchronisées pour un code d’attribut spécifique, procédez comme suit :

1. Utilisez la requête [!DNL SQL] suivante et vérifiez que vous disposez des données attendues dans la colonne `feed_data`. Notez également l’horodatage `modified_at`.

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Si vous ne voyez pas les données correctes, utilisez la commande suivante pour réindexer, puis exécutez à nouveau la requête [!DNL SQL] à l’étape 1 pour vérifier les données.

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. Si les données correctes ne s’affichent toujours pas, [créez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Vérifier l’horodatage de la dernière exportation d’attributs de produit

Si vous voyez les données correctes dans `cde_product_attributes_feed` :

1. Utilisez la requête [!DNL SQL] suivante pour vérifier l’horodatage de la dernière exportation. Elle doit être postérieure à l’horodatage `modified_at`.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Si l’horodatage est plus ancien, vous pouvez attendre la prochaine exécution cron ou le déclencher vous-même à l’aide de la commande suivante :

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Patientez 15 à 20 minutes (temps pour les mises à jour incrémentielles). Si vos données ne s’affichent toujours pas, veuillez [créer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Synchronisation après modification de la configuration de l’API

(Problème connu) Si vous avez modifié la configuration de votre API, ce qui entraîne une modification de votre identifiant d’espace de données, et que vous constatez que vos modifications de catalogue ne se synchronisent plus, exécutez les commandes suivantes pour resynchroniser les flux :

```
bin/magento saas:resync --feed productattributes --cleanup-feed
bin/magento saas:resync --feed products --cleanup-feed
bin/magento saas:resync --feed scopesCustomerGroup --cleanup-feed
bin/magento saas:resync --feed scopesWebsite --cleanup-feed
bin/magento saas:resync --feed prices --cleanup-feed
bin/magento saas:resync --feed productOverrides --cleanup-feed
bin/magento saas:resync --feed variants --cleanup-feed
bin/magento saas:resync --feed categories --cleanup-feed
bin/magento saas:resync --feed categoryPermissions --cleanup-feed
```

[Envoyez une demande d’assistance](https://experienceleague.adobe.com/home?lang=fr&support-tab=home#support) pour demander la réindexation de l’index Live Search. Dans la description du problème, incluez votre identifiant d’espace de données/d’environnement figurant dans le panneau d’administration sous **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Commerce Services Connector]**.

>[!IMPORTANT]
>N’utilisez l’option `--cleanup-feed` que si vous avez mis à jour la configuration de l’API ou si vous exécutez la commande `saas:resync` avec l’option [—dry-run](https://experienceleague.adobe.com/fr/docs/commerce/saas-data-export/data-export-cli-commands#--dry-run). Dans d’autres cas, l’utilisation de l’option `--cleanup-feed` entraîne des pertes de données et des problèmes de synchronisation des données.

## Lecture connexe

* [ Intégration de la recherche en direct ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html?lang=fr) dans notre documentation utilisateur
* [Consultez les journaux et résolvez les problèmes d’exportation et de synchronisation des données SaaS Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) dans le Guide d’exportation des données SaaS Adobe Commerce
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
