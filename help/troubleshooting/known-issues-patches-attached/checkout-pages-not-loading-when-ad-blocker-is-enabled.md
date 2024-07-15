---
title: Les pages d’extraction ne se chargent pas lorsque le bloqueur de publicités est activé
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.2 lié à l’échec du chargement des pages de passage en caisse provoqué par le bloc ou d’autres bloqueurs d’annonces.
exl-id: fe718f21-df23-4ab1-a6b0-03bad4d7095d
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Les pages d’extraction ne se chargent pas lorsque le bloqueur de publicités est activé

Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.2 lié à l’échec du chargement des pages de passage en caisse provoqué par le bloc ou d’autres bloqueurs d’annonces.

## Problème

Si Google Analytics est activé pour le magasin, lorsqu’un client avec un bloc ou un autre bloqueur d’annonces installé passe en caisse, le fichier `trackingCode.js` n’est pas chargé et RequireJS rompt le flux d’exécution JS. Cela entraîne des problèmes lors du chargement de la page de passage en caisse.

<u>Étapes à reproduire</u> :

Conditions préalables : un bloqueur d’annonces doit être installé et actif dans le navigateur.

1. Dans l’administrateur Commerce, activez et configurez la fonctionnalité Google Analytics.
1. Ouvrez une page de produit sur le storefront.
1. Ajoutez des produits au panier.
1. Cliquez sur le lien **Atteindre le passage en caisse** .

<u>Résultat attendu</u> : la page Passage en caisse se charge et le client peut terminer l’extraction.

<u>Résultat réel</u> : la page d’extraction ne se charge pas ; l’accélérateur de chargement ne disparaît jamais.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[Téléchargez MDVA-9353\_EE\_2.2.2\_v1.compositeur.patch.](assets/MDVA-9353_EE_2.2.2_v1.composer.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.2.2

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud de la version 2.1.0 à la version 2.1.14
* Adobe Commerce sur l’infrastructure cloud de la version 2.2.0 à la version 2.2.1 et de la version 2.2.3 à la version 2.2.5
* Adobe Commerce sur site de la version 2.1.0 à la version 2.1.14
* Adobe Commerce sur site de la version 2.2.0 à la version 2.2.5

## Comment appliquer le correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.

## Liens utiles

* [Problème discuté sur GitHub](https://github.com/magento/magento2/pull/13061)

## Fichiers attachés
