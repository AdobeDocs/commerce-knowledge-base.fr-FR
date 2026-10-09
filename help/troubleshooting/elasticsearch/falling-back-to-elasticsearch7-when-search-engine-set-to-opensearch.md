---
title: Retour à la [!DNL Elasticsearch7] lorsque le moteur de recherche est défini sur [!DNL Opensearch]
description: Cet article propose une solution au problème d’erreur « Retour à [!DNL Elasticsearch7] » lorsque le moteur de recherche est défini sur [!DNL OpenSearch] dans Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%
---
# Retour à la [!DNL Elasticsearch7] lorsque le moteur de recherche est défini sur [!DNL Opensearch]

Cet article fournit une solution au problème d’erreur *Retour à[!DNL Elasticsearch7]* qui se produit lorsque le moteur de recherche est défini sur [!DNL OpenSearch] dans Adobe Commerce.

## Versions affectées

Adobe Commerce sur les infrastructures cloud
2.4.4 - 2.4.4-p12
2.4.5 - 2.4.5-p11

>[!NOTE]
>
>[!DNL OpenSearch] est disponible en tant que moteur de recherche à partir d’Adobe Commerce 2.4.6, 2.4.5-p12, 2.4.4-p13.

## Problème

Vous définissez votre **moteur de recherche** sur **[!DNL OpenSearch]**, mais ce type d’erreur s’affiche dans le fichier `var/log/support_report.log` :

`[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []`

<u>Procédure à suivre </u> :

1. Vérifiez que [!DNL OpenSearch] est installé en exécutant la commande suivante : `curl 127.0.0.1:9200`<br>
S’il indique *1.2.4*, alors [!DNL OpenSearch] est déjà installé.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Vérifiez le moteur de recherche. Cela [!DNL Elasticsearch7]’affichera.

## Cause

Même si votre version prend en charge [!DNL OpenSearch], l’application ne reconnaîtra/acceptera que [!DNL Elasticsearch7] comme moteur de recherche.

À partir de la version 2.4.6 d’Adobe Commerce, l’application a été mise à jour afin de permettre la sélection de [!DNL OpenSearch] comme moteur de recherche.
Si vous accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** dans un environnement non cloud, vous pourrez modifier cette option comme indiqué dans l’**Solution** ci-dessous.
(Remarque : dans un environnement cloud, ce champ ne peut pas être modifié, car le moteur de recherche est verrouillé dans le fichier `app/etc/env.php`.)

## Solution

Mettez à jour la variable `SEARCH_CONFIGURATION` dans le fichier `.magento.env.yaml` et assurez-vous que le **moteur de recherche** est défini sur *[!DNL elasticsearch7]*.

## Lecture connexe

[Configurez le service OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) dans le guide Commerce sur les infrastructures cloud .
