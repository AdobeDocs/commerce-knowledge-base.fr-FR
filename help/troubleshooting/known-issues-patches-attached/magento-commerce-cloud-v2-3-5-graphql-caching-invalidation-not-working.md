---
title: L’invalidation de la mise en cache d’Adobe Commerce sur l’infrastructure cloud v2.3.5 GraphQL ne fonctionne pas
description: Cet article fournit un correctif pour le problème en raison duquel la requête "GET" de GraphQL renvoie des informations obsolètes si le client modifie les informations sur le produit.
exl-id: 10ae52bd-e71a-42e3-9600-7a9713903815
feature: GraphQL, Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# L’invalidation de la mise en cache d’Adobe Commerce sur l’infrastructure cloud v2.3.5 GraphQL ne fonctionne pas

Cet article fournit un correctif pour le problème de GraphQL `GET` request renvoie des informations obsolètes si le client modifie les informations sur le produit.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud v2.3.5.

## Problème

Les requêtes GraphQL sont mises en cache rapidement et la version mise en cache est récupérée pour chaque requête ultérieure à partir de Fastly. Lorsqu’un produit est réenregistré dans le serveur principal Adobe Commerce, le cache Fastly doit invalider lorsqu’un produit est mis à jour. Cependant, elle reste valide.

<u>Étapes à reproduire</u>:

1. Déclenchez la requête GraphQL suivante pour obtenir des produits pour certaines catégories, par exemple :
   <pre><magento2-server>
    </pre>
1. Enregistrez à nouveau l’un des produits récupérés par la requête ci-dessus dans l’administrateur Commerce.
1. Déclenchez à nouveau la requête.

<u>Résultats attendus</u>:

La variable `X-Cache` L’en-tête contient `MISS`.

<u>Résultats réels</u>:

La variable `X-Cache` L’en-tête contient `HIT`, ce qui signifie que la réponse est mise en cache.

## Solution

Désactivez le cache de produit GraphQL avec le correctif fourni dans cet article.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier ou cliquez sur le lien suivant :

[MDVA-28559\_EE\_2.3.5-p1\_COMPOSER\_v1.patch](assets/MDVA-28559_EE_2.3.5-p1_v1.composer.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud v2.3.5

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud v2.4.0
* Adobe Commerce sur site v2.4.0
* Adobe Commerce sur l’infrastructure cloud v2.3.5-p2
* Adobe Commerce sur site v2.3.5-p2
* Adobe Commerce sur l’infrastructure cloud v2.3.5-p1
* Adobe Commerce sur site v2.3.5-p1
* Adobe Commerce sur site v2.3.5
* Adobe Commerce sur l’infrastructure cloud v2.3.4-p2
* Adobe Commerce sur site v2.3.4-p2
* Adobe Commerce sur l’infrastructure cloud v2.3.4
* Adobe Commerce sur site v2.3.4
* Adobe Commerce sur site v2.3.3-p1
* Adobe Commerce sur site v2.3.3

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions sur la façon d’appliquer un correctif de compositeur.

## Fichiers attachés
