---
title: Comment contourner WAF pour les requêtes GraphQL
description: Cet article explique comment contourner WAF pour les requêtes GraphQL.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%
---
# Comment contourner WAF pour les requêtes GraphQL

Cet article explique comment contourner WAF pour les requêtes GraphQL lorsque le WAF [!DNL Fastly] bloque vos requêtes GraphQL.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud (toutes versions)

## Cause

En raison de la nature inhérente des requêtes GraphQL, il peut y avoir de nombreux caractères répétés qui peuvent déclencher un blocage faux positif des requêtes par le WAF [!DNL Fastly].

## Solution

1. Contournez le WAF pour ces requêtes en ajoutant un fragment de code personnalisé via le module Magento [!DNL Fastly] :

   type : recv
   priorité : 15
   contenu :

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Cliquez sur **[!UICONTROL Upload VCL to Fastly]**.

## Lecture connexe

* Guide [Web Application Firewall (WAF)](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) dans Commerce on Cloud Infrastructure.
* [Guide de prise en main d’un VCL personnalisé](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) dans Commerce sur les infrastructures cloud .
