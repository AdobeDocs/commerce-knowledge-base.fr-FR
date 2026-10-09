---
title: Impossible de voir plusieurs espaces de données SaaS après la configuration des clés API Adobe AI
description: Cet article fournit une solution aux problèmes où vous ne voyez qu’un seul espace de données SaaS après avoir configuré les clés API pour Adobe AI.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d3b92bef-63fa-5031-a925-d04d9362d616
    internal-label: Saas
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%
---
# Impossible de voir plusieurs espaces de données SaaS après la configuration des clés API Adobe AI

Après avoir configuré les clés d’API pour un service Commerce tel que les services Adobe AI (Recommandations de produits ou Recherche en direct) ou les services de paiement pour Adobe Commerce, vous vous attendez à voir plusieurs espaces de données SaaS dans le connecteur de services Commerce. Selon les droits du produit et le type de déploiement, le connecteur affiche un seul espace de données SaaS, ce qui est le comportement attendu.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) : toutes les versions
* Magento Open Source : toutes les versions
* Extension ou technologie (Fastly, New Relic, etc.), Adobe AI (Product Recommendations/Live Search)

## Problème

Après avoir configuré les clés API Adobe AI, le système n’affiche qu’un seul espace de données SaaS.

## Cause

Le nombre d’espaces de données SaaS disponibles dépend des droits du produit liés au compte Commerce et du type de service utilisé.

## Solution

En règle générale, le nombre d’espaces de données SaaS disponibles dépend de la licence Commerce :

* Adobe Commerce : un espace de données de production et deux espaces de données de test
* Magento Open Source : un espace de données de production et aucun espace de données de test

Pour Payment Services, le comportement par défaut est le suivant :

* Payment Services sur Adobe Commerce (*Cloud ou On-premise*) dispose par défaut de trois espaces de données :
* un espace de données de production
* deux espaces de données de test
* Payment Services sur Magento Open Source comporte un espace de données par défaut

Les clients qui possèdent plusieurs projets cloud ou installations sur site (*en ligne/de production*) peuvent également demander des espaces de données de production et de test supplémentaires pour chaque projet ou instance en envoyant une demande d’assistance.

Les clients Magento Open Source qui utilisent les services de paiement Adobe peuvent également demander un espace de données supplémentaire. Contactez l’équipe des paiements pour une approbation préalable avant d’envoyer une demande d’assistance pour ajouter un espace de données de test.

>[!NOTE]
> * N’utilisez pas le même espace de données SaaS dans plusieurs environnements en même temps. Si un espace de données de production ou de test est réutilisé dans les environnements, les données peuvent devenir mixtes et nécessiter un nettoyage.
> * Les services de paiement sur Adobe Commerce (*Cloud/On-Prem*) disposent par défaut de trois espaces de données.
> * Les services de paiement sur Magento Open Source disposent par défaut d’un seul espace de données.
> Pour demander des espaces de données supplémentaires :
> * Les clients Magento Open Source qui utilisent les services de paiement Adobe peuvent demander un espace de données supplémentaire. Contactez l’équipe des paiements pour une approbation préalable avant d’envoyer une demande d’assistance pour obtenir un espace de données de test.
> * Les clients qui possèdent plusieurs projets cloud ou installations sur site (*en ligne/de production*) peuvent également demander des espaces de données de production et de test supplémentaires pour chaque projet ou instance en envoyant une demande d’assistance.

## Lecture connexe

[Approvisionnement de l’espace de données SaaS](https://experienceleague.adobe.com/en/docs/commerce/user-guides/integration-services/saas?lang=en#saas-data-space-provisioning)
