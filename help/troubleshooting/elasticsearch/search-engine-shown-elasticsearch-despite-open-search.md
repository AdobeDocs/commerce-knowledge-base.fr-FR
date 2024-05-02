---
title: '[!DNL Elasticsearch] s’affiche en tant que moteur de recherche, malgré [!DNL OpenSearch] installation'
description: Cet article fournit une solution au problème où [!DNL Elasticsearch] s’affiche toujours comme moteur de recherche pour Adobe Commerce dans le cloud, même après l’installation ou la mise à niveau vers [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1a36e74807e6d32b0810416b6fb61aeca6f9be94
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# [!DNL Elasticsearch] s’affiche en tant que moteur de recherche, malgré [!DNL OpenSearch] installation

Cet article fournit une solution au problème où [!DNL Elasticsearch] s’affiche toujours comme moteur de recherche pour Adobe Commerce dans le cloud, même après l’installation ou la mise à niveau vers [!DNL OpenSearch].

## Versions affectées

Adobe Commerce sur cloud 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>[!DNL OpenSearch] est disponible en tant que moteur de recherche à partir d’Adobe Commerce 2.4.6.

## Problème

[!DNL Elasticsearch] s’affiche toujours comme moteur de recherche pour Adobe Commerce dans le cloud, même après l’installation ou la mise à niveau vers [!DNL OpenSearch].

<u>Étapes à reproduire</u>:

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Vérifiez le moteur de recherche. Elle s’affiche. [!DNL Elasticsearch7].

## Cause

Adobe Commerce est codé en dur pour spécifier les [!DNL Elasticsearch7] comme moteur de recherche.

## Solution

Pour vérifier si [!DNL OpenSearch] a été installé, exécutez la commande suivante :

**Méthode 1**:

* Exécutez la commande suivante sur le serveur : `curl 127.0.0.1:9200`. Elle doit être renvoyée. [!DNL OpenSearch] avec sa version.

**Méthode 2**:

* Utilisez la commande suivante sur l’interface de ligne de commande de Magento-cloud : `magento-cloud relationships -p <project_id>`. Après avoir utilisé la commande , localisez [!DNL OpenSearch].

## Lecture connexe

[Configuration du service OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) dans le guide Commerce on Cloud Infrastructure.
