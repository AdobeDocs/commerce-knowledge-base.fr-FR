---
title: Obtention de milliers de résultats lors de la recherche d’un produit spécifique
description: 'Cet article fournit une solution au problème suivant : lorsque vous recherchez un produit particulier, vous obtenez des milliers de résultats de recherche.'
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 792a7e9b-6519-5e99-a913-56c3dd2408da
    internal-label: Quotes
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%
---
# Obtention de milliers de résultats lors de la recherche d’un produit spécifique

Cet article fournit une solution au problème où vous obtenez des milliers de résultats de recherche lorsque vous recherchez un produit particulier.

## Produits et versions concernés

* Adobe Commerce toutes les versions avec [!DNL ElasticSearch] installé

## Événements

Vous recherchez un produit particulier (par exemple, *WSH12-32-Red*), mais la recherche renvoie de nombreux produits similaires.

## Solutions

La nature d’une recherche en texte intégral dans [!DNL ElasticSearch] repose sur la pertinence, et non sur la correspondance exacte. Ainsi, la plupart des correspondances pertinentes (comme le SKU correspondant exact) sont commandées en premier.

Cependant, si vous avez besoin d’un résultat de recherche qui correspond exactement à votre terme de recherche (correspondance exacte), vous devez utiliser des guillemets pour votre requête. Par exemple, une requête pour *WSH12-32-Red* sans guillemets renvoie plusieurs résultats avec la correspondance exacte (produit avec *SKU WSH12-32-Red*) apparaissant en premier dans le résultat. Mais la requête entre guillemets *« WSH12-32-Red »* ne renverra qu’un seul résultat de correspondance exact.
