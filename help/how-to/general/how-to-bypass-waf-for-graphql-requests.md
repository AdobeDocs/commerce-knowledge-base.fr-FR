---
title: Comment contourner le WAF pour les requêtes GraphQL
description: Cet article explique comment contourner le WAF pour les requêtes GraphQL.
feature: GraphQL
source-git-commit: c35d4ba82fbe1657756e160a73fd575c736b4e1c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Comment contourner le WAF pour les requêtes GraphQL

Cet article explique comment contourner le WAF pour les requêtes GraphQL lorsque la variable [!DNL Fastly] Le WAF bloque vos requêtes GraphQL.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud (toutes versions)

## Cause

En raison de la nature inhérente des requêtes GraphQL, de nombreux caractères répétés peuvent déclencher un blocage faux positif des requêtes par la variable [!DNL Fastly] WAF.

## Solution

1. Contournement de la méthode WAF pour ces requêtes en ajoutant un fragment de code personnalisé par le biais de la fonction [!DNL Fastly] Module Magento :

   type : priorité recv : 15 contenus :

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Cliquez sur **[!UICONTROL Upload VCL to Fastly]**.

## Lecture connexe

* [Web Application Firewall (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) dans le guide Commerce on Cloud Infrastructure.
* [Prise en main de VCL personnalisé](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) dans le guide Commerce on Cloud Infrastructure.

