---
title: J’ai configuré les clés API pour l’IA d’Adobe, mais je ne vois qu’un seul espace de données SaaS
description: Cet article fournit une solution aux problèmes où vous ne voyez qu’un seul espace de données SaaS après avoir configuré les clés API pour l’IA dédiée à Adobe.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 27b0836380c3040b26076b9cb81b9328cb2c9ff2
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# J’ai configuré les clés API pour l’IA d’Adobe, mais je ne vois qu’un seul espace de données SaaS

Cet article fournit une solution aux problèmes où vous ne voyez qu’un seul espace de données SaaS après avoir configuré les clés API pour l’IA dédiée à Adobe.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) : toutes les versions
* Magento Open Source : toutes les versions
* Extension ou technologie (Fastly, New Relic, etc.), Adobe AI (Product Recommendations/Live Search)

## Problème

J’ai configuré les clés d’API pour l’IA dédiée à Adobe, mais je ne vois qu’un seul espace de données SaaS.

## Cause

Le nombre d’espaces de données SaaS qui s’affichent dépend de votre licence Commerce :

* Adobe Commerce : un espace de données de production ; deux espaces de données de test.
* Magento Open Source - Un espace de données de production ; aucun espace de données de test

## Solution

* Assurez-vous que les clés API ont été créées sur le compte du propriétaire du compte. Même si vous avez reçu un accès partagé à leur compte et que vous avez créé les clés sur votre propre compte, vous ne disposerez pas de plus d’un espace de données.
* Si les clés ont été générées sur le compte du titulaire du compte, assurez-vous que la licence est active, c’est-à-dire qu’il n’y a aucune facture en attente.
