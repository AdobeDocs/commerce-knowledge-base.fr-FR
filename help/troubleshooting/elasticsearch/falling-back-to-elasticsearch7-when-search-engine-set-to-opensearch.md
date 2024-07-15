---
title: Revenir à  [!DNL Elasticsearch7]  lorsque le moteur de recherche est défini sur  [!DNL Opensearch]
description: Cet article fournit une solution au problème lorsqu’un appel *Revenir à [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] dans Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Revenir à [!DNL Elasticsearch7] lorsque le moteur de recherche est défini sur [!DNL Opensearch]

Cet article fournit une solution au problème lorsqu’une erreur *Revenir à[!DNL Elasticsearch7]* se produit lorsque le moteur de recherche est défini sur [!DNL OpenSearch] dans Adobe Commerce.

## Versions affectées

Adobe Commerce sur l’infrastructure cloud 2.4.4 - 2.4.5

>[!NOTE]
>
>[!DNL OpenSearch] est disponible comme moteur de recherche à partir d’Adobe Commerce 2.4.6.

## Problème

Vous définissez votre **moteur de recherche** sur **[!DNL OpenSearch]**, mais voyez ce type d’erreur dans le fichier `var/log/support_report.log` :

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>Étapes à reproduire</u> :

1. Vérifiez que [!DNL OpenSearch] est installé en exécutant cette commande : `curl 127.0.0.1:9200`<br>
S’il indique *1.2.4*, alors [!DNL OpenSearch] est déjà installé.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Vérifiez le moteur de recherche. Il affichera [!DNL Elasticsearch7].

## Cause

Même si votre version ne prend pas en charge [!DNL OpenSearch], l’application reconnaît/accepte uniquement [!DNL Elasticsearch7] comme moteur de recherche.

Depuis la version 2.4.6 d’Adobe Commerce, l’application a été mise à jour afin que [!DNL OpenSearch] puisse être sélectionné comme moteur de recherche.
Si vous accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** dans un environnement autre que cloud, vous pourrez modifier cette option comme illustré dans la **solution** ci-dessous.
(Remarque : dans un environnement cloud, ce champ ne peut pas être modifié car le moteur de recherche est verrouillé dans le fichier `app/etc/env.php`.)

## Solution

Mettez à jour la variable `SEARCH_CONFIGURATION` dans le fichier `.magento.env.yaml` et assurez-vous que le **moteur de recherche** est défini sur *[!DNL elasticsearch7]*.

## Lecture connexe

[ Configurez le service OpenSearch ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) dans le guide Commerce on Cloud Infrastructure.
