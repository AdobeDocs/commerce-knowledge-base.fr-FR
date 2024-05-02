---
title: J’ai configuré des clés d’API pour Sensei, mais je ne vois qu’un seul espace de données SaaS.
description: Cet article fournit une solution pour les problèmes où un seul espace de données SaaS s’affiche une fois que vous avez configuré les clés d’API pour Sensei.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# J’ai configuré des clés d’API pour Sensei, mais je ne vois qu’un seul espace de données SaaS.

Cet article fournit une solution pour les problèmes où un seul espace de données SaaS s’affiche une fois que vous avez configuré les clés d’API pour Sensei.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) : toutes les versions
* Magento Open Source : toutes les versions
* Extension ou technologie (Fastly, New Relic, etc.), Adobe Sensei (Recommendations de produit/Recherche en direct)

## Problème

J’ai configuré les clés d’API pour Sensei, mais je ne vois qu’un seul espace de données SaaS.

## Cause

Le nombre d’espaces de données SaaS qui apparaissent dépend de votre licence Commerce :

* Adobe Commerce : un espace de données de production ; deux espaces de données de test
* Magento Open Source : un espace de données de production ; aucun espace de données de test

## Solution

* Assurez-vous que les clés d’API ont été créées sur le compte du titulaire du compte. Même si l’accès partagé à leur compte vous a été accordé et que vous avez créé les clés sur votre propre compte, cela ne vous accordera pas plus d’un espace de données.
* Si les clés ont été générées sur le compte du titulaire du compte, assurez-vous que la licence est active, c’est-à-dire qu’il n’y a aucune facture en attente.
