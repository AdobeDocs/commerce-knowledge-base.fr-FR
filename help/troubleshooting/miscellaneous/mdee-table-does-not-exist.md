---
title: Correction des données non mises à jour dans les flux  [!DNL Commerce Data Exporter] et les erreurs de  [!DNL cron] logs avec la table changelog n'existent pas
description: Cet article fournit une solution pour résoudre les problèmes de synchronisation des données provoqués par l’utilisation d’un ID d’affichage incorrect dans l’abonnement  [!DNL Commerce Data Exporter mview] .
feature: Data Import/Export, Saas, Logs
role: Developer
exl-id: 50f2223b-bfcf-4c3c-b0f1-dbcc4365edc2
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Correction des données non mises à jour dans les flux [!DNL Commerce Data Exporter] et des erreurs de journaux [!DNL cron] avec la table changelog qui n&#39;existent pas

Cet article fournit une solution pour résoudre les problèmes de synchronisation des données provoqués par l’utilisation d’un identifiant d’affichage incorrect dans l’abonnement [!DNL Data Exporter] [[!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview). L&#39;abonnement [!DNL Mview] est utilisé pour effectuer le suivi des modifications des tables de base de données.

## Produits et versions concernés

Instances Adobe Commerce où du code personnalisé a été appliqué à la fonctionnalité d’exportation de données (`commerce-data-exporter` ou `saas-exporter`). L’erreur se produit si la version [[!DNL SaaS] Exportation de données installée est 103.3.0](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/saas-data-export/release-notes#release-6) ou supérieure, et que le code fait directement référence à l’index `catalog_data_exporter_products`.

## Problème

Les vendeurs peuvent constater que les mises à jour de données sont manquantes dans les tables de flux Catalog [!DNL Data Exporter] et voir les erreurs suivantes dans les journaux de tâches [!DNL cron] :

```
[2024-05-27T19:00:04.627604+00:00] report.ERROR: Cron Job indexer_clean_all_changelogs has an error: Table catalog_data_exporter_products_cl does not exist. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":305135616,"emalloc_start":283210384} [] [] 
```

## Cause

En raison de changements de nom dans les tables de flux, les index et les tables de journaux de modification dans la version [!DNL Commerce Data Export] [&#x200B; 103.3.0](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/saas-data-export/release-notes#release-9), les abonnements [!DNL Mview] dans les extensions personnalisées qui utilisent les extensions [!DNL Commerce Data Export] peuvent ne pas fonctionner correctement.

Dans ce cas, l&#39;erreur *table n&#39;existe pas* se produit car le nom de la table `catalog_data_exporter` a été remplacé par `cde_products_feed` et vous avez un code personnalisé qui référence l&#39;ancien nom dans l&#39;abonnement [!DNL Data Exporter Mview].

## Solution

Dans l’extension personnalisée, modifiez le fichier de configuration [!DNL Mview] (```./etc/mview.xml```) pour remplacer le nom de la table `catalog_data_exporter_products` par *`cde_products_feed`*.

L’exemple suivant montre le code qui spécifie les tables suivies par l’abonnement [!DNL Mview] :

```
<view id="cde_products_feed" class="Magento\CatalogDataExporter\Model\Indexer\ProductFeedIndexer" group="indexer">
     <subscriptions>
         <table name="custom_table" entity_column="product_id" />
     </subscriptions>
</view>
```

## Lecture connexe

* [[!DNL SaaS] Notes de mise à jour de l’extension d’exportation de données](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/saas-data-export/release-notes) dans le guide d’exportation de données Adobe Commerce pour les services [!DNL SaaS]
* [&#x200B; Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
