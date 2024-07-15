---
title: Obtention de milliers de résultats lors de la recherche d’un produit spécifique
description: Cet article fournit une solution au problème où vous obtenez des milliers de résultats de recherche lorsque vous recherchez un produit particulier.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Obtention de milliers de résultats lors de la recherche d’un produit spécifique

Cet article fournit une solution au problème où vous obtenez des milliers de résultats de recherche lorsque vous recherchez un produit particulier.

## Produits et versions concernés

* Adobe Commerce : toutes les versions avec [!DNL ElasticSearch] installé

## Problèmes

Vous recherchez un produit particulier (par exemple, *WSH12-32-Red*), mais la recherche renvoie de nombreux produits similaires.

## Solutions

La nature d’une recherche de texte intégral dans [!DNL ElasticSearch] repose sur la pertinence, et non sur une correspondance exacte. Ainsi, les correspondances les plus pertinentes (comme le SKU correspondant exact) sont commandées en premier.

Cependant, si vous avez besoin d’un résultat de recherche qui correspond exactement à votre terme de recherche (correspondance exacte), vous devez utiliser des guillemets pour votre requête. Par exemple, la requête de *WSH12-32-Red* sans guillemets renvoie plusieurs résultats avec une correspondance exacte (produit avec *SKU WSH12-32-Red*) apparaissant en premier dans le résultat. Mais la requête entre guillemets *&quot;WSH12-32-Red&quot;* ne renvoie qu’un seul résultat de correspondance exact.
