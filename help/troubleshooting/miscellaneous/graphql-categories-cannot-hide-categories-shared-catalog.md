---
title: Requête GraphQL pour masquer les catégories qui ne fonctionnent pas avec le catalogue partagé B2B
description: Cet article fournit une solution pour les cas où la fonctionnalité de catalogue partagé B2B ne fonctionne pas avec la requête de catégories GraphQL pour masquer les catégories.
exl-id: bdafa8d9-b637-409e-86b5-d132bccfe0b8
feature: B2B, Catalog Management, Categories, GraphQL, Customer Service
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Requête GraphQL pour masquer les catégories qui ne fonctionnent pas avec le catalogue partagé B2B


## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.4.3

## Problème

Les catégories GraphQL et les requêtes `categoryList` ignorent l’autorisation de catégorie pour masquer les catégories dans un catalogue partagé. Cela se produit pour tous les commerçants sur Adobe Commerce 2.4.3 avec la fonction Catalogue partagé B2B activée.

<u>Étapes à reproduire</u> :

Conditions préalables :

Cela se produit pour tous les commerçants sur Adobe Commerce 2.4.3. Le storefront du PWA utilise l’API GraphQL avec le serveur principal/l’administrateur d’Adobe Commerce avec la fonction Catalogue partagé B2B activée.

1. Créez plusieurs catégories (CAT1, CAT2).
1. Créez un catalogue partagé privé.
1. Créez un utilisateur de société et affectez-le au catalogue partagé ci-dessus.
1. Attribuez quelques produits à chacune de ces catégories.
1. Affectez CAT1 au catalogue personnalisé, annulez l’affectation de CAT2 au catalogue privé personnalisé. Cela annule l’attribution de tous les produits de CAT2 du catalogue partagé.
1. Enregistrez le catalogue personnalisé.
1. Définissez l’autorisation de catégorie pour CAT2 sur *Refuser* catégorie de navigation et définissez le groupe de clients sur le catalogue privé ci-dessus.
1. Exécutez la requête `categoryList query` ou les catégories en tant qu’utilisateur de l’entreprise à partir de l’étape 3.

<u>Résultats attendus</u> :

Seul le CAT1 apparaît dans les résultats.

<u>Résultats réels</u> :

Toutes les catégories s’affichent, qu’elles soient affectées/non affectées dans le catalogue partagé ou que les autorisations de catégorie soient accordées.

## Cause

La fonctionnalité n’a pas été mise en oeuvre.

## Solution

Le problème va être résolu dans la portée de la version 2.4.4, et les vendeurs doivent [envoyer un ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour obtenir un correctif personnalisé s’ils ont besoin d’une solution avant la version 2.4.4.

## Lecture connexe

* [Les bonnes pratiques Adobe Commerce limitent le nombre de catégories](https://support.magento.com/hc/en-us/articles/360048176832) dans notre base de connaissances de support.
