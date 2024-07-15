---
title: La recherche de correspondance exacte ne fonctionne pas dans Adobe Commerce 2.4.x
description: Cet article fournit une clarification sur le problème de différence entre les résultats de la recherche frontale du magasin utilisant la même chaîne de recherche dans Adobe Commerce 2.4.x et Adobe Commerce 2.3.x.
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# La recherche de correspondance exacte ne fonctionne pas dans Adobe Commerce 2.4.x

Cet article fournit une clarification sur le problème de différence entre les résultats de la recherche frontale du magasin utilisant la même chaîne de recherche dans Adobe Commerce 2.4.x et Adobe Commerce 2.3.x.

## Produits et versions concernés

- Adobe Commerce (toutes les méthodes de déploiement) 2.4.x, 2.3.x
- Recherche en direct

## Problème

<u>Conditions préalables :</u>

Vous avez des produits avec des valeurs d’attribut `Saga 1` et `Saga 16` dans les magasins Adobe Commerce 2.3 et Adobe Commerce 2.4.

<u>Étapes à reproduire :</u>

1. Sur le devant d’un magasin Adobe Commerce 2.3, saisissez *Saga 1* dans le champ de recherche et cliquez sur **Rechercher**.
1. Notez que dans les résultats de recherche, vous obtenez uniquement les produits avec la valeur d’attribut `Saga 1`.
1. Sur le devant d’un magasin Adobe Commerce 2.4, saisissez *Saga 1* dans le champ de recherche et cliquez sur **Rechercher**.

<u>Résultat réel :</u>

Dans la version 2.4, les résultats de recherche incluent les produits avec des valeurs d’attribut `Saga 1` et `Saga 16`.

<u>Résultat attendu :</u>

Les résultats de recherche dans la version 2.4 sont similaires à la version 2.3 et incluent uniquement les produits avec la valeur d’attribut `Saga 1`.

## Cause

La fonctionnalité de recherche native d’Adobe Commerce utilisée dans la version 2.3.x fournit des résultats de recherche avec correspondance exacte. Lors de la recherche en direct, un module facultatif disponible pour l’installation, qui a été publié avec Adobe Commerce 2.4.x, est implémenté différemment, et le résultat réel est le comportement attendu lorsque le module est utilisé.

## Lecture connexe

[Installez Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) dans notre guide d’utilisation.

[Recherche en direct](https://devdocs.magento.com/live-search/overview.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=Live%20Search) dans la documentation destinée aux développeurs.
