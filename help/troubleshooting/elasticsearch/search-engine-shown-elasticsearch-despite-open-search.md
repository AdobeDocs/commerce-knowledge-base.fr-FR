---
title: '[!DNL Elasticsearch] s’affiche comme le moteur de recherche malgré  [!DNL OpenSearch] ’installation'
description: Cet article fournit une solution au problème où  [!DNL Elasticsearch]  s’affiche toujours comme moteur de recherche pour Adobe Commerce sur le cloud, même après l’installation ou la mise à niveau vers  [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: b3f68e43ce3c4fdea001db1d8ba2774900db7dba
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL Elasticsearch] s’affiche comme le moteur de recherche malgré [!DNL OpenSearch] installation

Cet article fournit une solution au problème où [!DNL Elasticsearch] s’affiche toujours en tant que moteur de recherche pour Adobe Commerce sur le cloud, même après l’installation ou la mise à niveau vers [!DNL OpenSearch].

## Versions affectées

Adobe Commerce on cloud 2.4.4 - 2.4.5-p11

>[!NOTE]
>
>[!DNL OpenSearch] est disponible sous la forme d’un moteur de recherche à partir d’Adobe Commerce 2.4.6.

## Problème

[!DNL Elasticsearch] s’affiche toujours en tant que moteur de recherche pour Adobe Commerce sur le cloud, même après l’installation ou la mise à niveau vers [!DNL OpenSearch].

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Vérifiez le moteur de recherche. Cela [!DNL Elasticsearch7]’affichera.

## Cause

[!DNL Elasticsearch7] est codé en dur dans Adobe Commerce pour être le moteur de recherche utilisé dans ces versions.

À ne pas confondre avec la version installée du service. Bien qu’il n’y ait pas de module [!DNL Opensearch] inclus dans le code, Adobe Commerce peut utiliser le service de [!DNL Opensearch] sous-jacent.

## Solution

Pour vérifier si [!DNL OpenSearch] a été installé, exécutez la commande suivante :

**Méthode 1** :

* Exécutez la commande suivante sur le serveur : `curl 127.0.0.1:9200`. Il doit renvoyer [!DNL OpenSearch] avec sa version.

Exemple :

```
$ curl 127.0.0.1:9200
{
  "name" : $clusterName,
  "cluster_name" : "opensearch_stg",
  "cluster_uuid" : $clusterUuid,
  "version" : {
    "distribution" : "opensearch",
    "number" : "1.2.4",
    "build_type" : "deb",
    "build_hash" : "44ccdbaed5fe5a8b02d99a611857a671b6dd909d",
    "build_date" : "2022-11-08T09:23:45.993372Z",
    "build_snapshot" : false,
    "lucene_version" : "8.10.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "The OpenSearch Project: https://opensearch.org/"
}
```

**Méthode 2** :

* Utilisez la commande suivante sur l’interface de ligne de commande Magento-cloud : `magento-cloud relationships -p <project_id>`. Après avoir utilisé la commande , localisez [!DNL OpenSearch].

## Lecture connexe

[Configurez le service OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) dans le guide Commerce sur les infrastructures cloud .
