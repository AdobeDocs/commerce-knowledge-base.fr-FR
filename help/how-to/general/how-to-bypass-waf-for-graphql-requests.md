---
title: Comment contourner le WAF pour les requêtes GraphQL
description: Cet article explique comment contourner le WAF pour les requêtes GraphQL.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
source-git-commit: 2bec86818336a9ef4d8316e257a0ca4256cdd93c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Comment contourner le WAF pour les requêtes GraphQL

Cet article explique comment contourner le WAF pour les requêtes GraphQL lorsque le WAF [!DNL Fastly] bloque vos requêtes GraphQL.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud (toutes versions)

## Cause

En raison de la nature inhérente des requêtes GraphQL, il peut y avoir beaucoup de caractères répétés qui peuvent déclencher un blocage faux positif des requêtes par le WAF [!DNL Fastly].

## Solution

1. Contournez la méthode WAF pour ces requêtes en ajoutant un fragment de code personnalisé par le biais du module de Magento [!DNL Fastly] :

   type : recv
priorité : 15
content :

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Cliquez sur **[!UICONTROL Upload VCL to Fastly]**.

## Lecture connexe

* [Web Application Firewall (WAF)](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) dans le guide Commerce on Cloud Infrastructure.
* [Prise en main de VCL](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) personnalisé dans le guide Commerce on Cloud Infrastructure.
