---
title: Comment contourner WAF pour les requêtes GraphQL
description: Cet article explique comment contourner WAF pour les requêtes GraphQL.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
source-git-commit: 2bec86818336a9ef4d8316e257a0ca4256cdd93c
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

1. Contournez le WAF pour ces requêtes en ajoutant un fragment de code personnalisé via le module [!DNL Fastly] Magento :

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

* Guide [Web Application Firewall (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) dans Commerce on Cloud Infrastructure.
* [Guide de prise en main d’un VCL personnalisé](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) dans Commerce sur les infrastructures cloud .
