---
title: Correction des erreurs de données non mises à jour dans  [!DNL Commerce Data Exporter]  flux et les journaux  [!DNL cron]  avec la table changelog qui n'existe pas
description: Cet article fournit une solution pour résoudre les problèmes de synchronisation des données causés par l’utilisation d’un ID de vue incorrect dans l [!DNL Commerce Data Exporter mview] abonnement.
feature: Data Import/Export, Saas, Logs
role: Developer
exl-id: 50f2223b-bfcf-4c3c-b0f1-dbcc4365edc2
source-git-commit: 40766238a7ea748bff86decf75cddec28fe63bb9
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Les données de correctif non mises à jour dans les flux [!DNL Commerce Data Exporter] et les erreurs de journaux [!DNL cron] avec la table changelog n&#39;existent pas

Cet article fournit une solution pour résoudre les problèmes de synchronisation des données causés par l’utilisation d’un ID de vue incorrect dans l’abonnement à [!DNL Data Exporter] [[!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview). L&#39;abonnement [!DNL Mview] est utilisé pour effectuer le suivi des modifications des tables de la base de données.

## Produits et versions concernés

Instances Adobe Commerce sur lesquelles un code personnalisé a été appliqué à la fonctionnalité d’exportation de données (`commerce-data-exporter` ou `saas-exporter`). L’erreur se produit si la version [[!DNL SaaS] Exportation de données) installée est 103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-6) ou ultérieure et que le code fait directement référence à l’index `catalog_data_exporter_products`.

## Problème

Les commerçants peuvent constater que les mises à jour de données sont absentes des tables de flux de l’[!DNL Data Exporter] Catalogue et voir les erreurs suivantes dans les journaux de tâches [!DNL cron] :

```
[2024-05-27T19:00:04.627604+00:00] report.ERROR: Cron Job indexer_clean_all_changelogs has an error: Table catalog_data_exporter_products_cl does not exist. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":305135616,"emalloc_start":283210384} [] [] 
```

## Cause

En raison des changements de nom dans les tables de flux, les index et les tables de logs des modifications dans la version [!DNL Commerce Data Export] [version 103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-9), les abonnements [!DNL Mview] dans les extensions personnalisées qui utilisent les extensions [!DNL Commerce Data Export] peuvent ne pas fonctionner correctement.

Dans ce cas, l&#39;erreur *table n&#39;existe pas* se produit car le nom de la table `catalog_data_exporter` a été modifié en `cde_products_feed` et vous disposez d&#39;un code personnalisé qui fait référence à l&#39;ancien nom dans l&#39;abonnement [!DNL Data Exporter Mview].

## Solution

Dans l’extension personnalisée, modifiez le fichier de configuration [!DNL Mview] (`./etc/mview.xml`) pour remplacer le nom de la table `catalog_data_exporter_products` par *`cde_products_feed`*.

L’exemple suivant illustre le code qui spécifie les tables suivies par l’abonnement [!DNL Mview] :

```
<view id="cde_products_feed" class="Magento\CatalogDataExporter\Model\Indexer\ProductFeedIndexer" group="indexer">
     <subscriptions>
         <table name="custom_table" entity_column="product_id" />
     </subscriptions>
</view>
```

## Lecture connexe

* [[!DNL SaaS] Notes de mise à jour de l’extension Data Export](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes) dans le Guide d’exportation de données Adobe Commerce pour [!DNL SaaS] Services
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
