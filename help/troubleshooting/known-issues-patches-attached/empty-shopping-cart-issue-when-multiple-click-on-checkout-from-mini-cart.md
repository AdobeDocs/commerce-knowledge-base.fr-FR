---
title: Problème de panier vide lorsque plusieurs clics sur le passage en caisse depuis le mini panier
description: Cet article fournit un correctif pour un problème connu d’Adobe Commerce 2.2.3 lié au fait qu’un panier est vide lorsque les clients cliquent plusieurs fois sur **Atteindre le passage en caisse** dans le mini panier.
exl-id: 06b82c91-8998-4e7b-9fc0-671c9b2a2d3f
feature: Checkout, Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# Problème de panier vide lorsque plusieurs clics sur le passage en caisse depuis le mini panier

Cet article fournit un correctif pour un problème connu d’Adobe Commerce 2.2.3 lié à un panier vide après que les clients ont cliqué sur **Aller à la caisse** plusieurs fois dans le mini panier.

## Problème

Les clients ajoutent des produits au panier, essaient de les extraire en cliquant sur le bouton **Aller à la caisse** plusieurs fois, mais lorsqu’ils accèdent au panier, celui-ci est vide. Le mini-panier peut toujours afficher les produits.

<u>Étapes à reproduire</u> :

1. Ouvrez une page de produit au premier plan du magasin.
1. Ajoutez des produits au panier.
1. Dans le mini panier, cliquez sur **Aller à la caisse** plusieurs fois.

<u>Résultat attendu</u> :

Le panier contient tous les produits que vous avez ajoutés.

<u>Résultat réel</u> :

Vous n&#39;avez aucun article dans votre panier.

## Correctif

Les correctifs sont joints à cet article. Pour télécharger un correctif, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom de fichier requis ou cliquez sur l’un des liens suivants :

[Téléchargez MDVA-10441\_EE\_2.2.3\_v3.compositeur.patch.](assets/MDVA-10441_EE_2.2.3_v3.composer.patch.zip)

[Téléchargez MDVA-17078\_EE\_2.2.5\_COMPOSER\_v1.patch.](assets/MDVA-17078_EE_2.2.5_COMPOSER_v1.patch.zip)

### Versions Adobe Commerce compatibles

Les correctifs ont été créés pour :

* Adobe Commerce on-premise 2.2.3 (le `MDVA-10441_EE_2.2.3_v3.composer.patch` fichier)
* Adobe Commerce sur l’infrastructure cloud 2.2.5 (`MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` fichier)

La variable `MDVA-10441_EE_2.2.3_v3.composer.patch` Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur les versions d’infrastructure cloud de la version 2.2.1 à la version 2.2.5
* Versions sur site d’Adobe Commerce de 2.2.1 à 2.2.5

La variable `MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce 2.2.5

## Comment appliquer un correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de soutien.

## Fichiers attachés
