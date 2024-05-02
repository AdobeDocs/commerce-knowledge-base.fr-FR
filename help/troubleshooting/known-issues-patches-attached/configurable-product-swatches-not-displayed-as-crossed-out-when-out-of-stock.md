---
title: Échantillons de produits configurables non affichés en rupture de stock
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.2 lié aux échantillons de produits configurables en rupture de stock qui ne s’affichent pas comme barré sur le storefront.
exl-id: 79c59a3f-a94b-4726-8af1-5fe754ea95a5
feature: Configuration, Orders, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Échantillons de produits configurables non affichés en rupture de stock

Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.2 lié aux échantillons de produits configurables en rupture de stock qui ne s’affichent pas comme barré sur le storefront.

## Problème

Lorsque vous disposez d’un produit configurable et que, pour une certaine combinaison d’options, le produit simple associé est en rupture de stock, l’échantillon est toujours disponible et peut être sélectionné sur le storefront.

<u>Étapes à reproduire</u>:

1. Dans l’administrateur Commerce, créez un produit configurable avec des options pour deux attributs : couleur (rouge, noir) et taille (S, M, L).
1. Définissez Quantité sur &quot;1&quot; pour chaque produit simple correspondant.
1. Sur le storefront, ajoutez le produit rouge M au panier et au passage en caisse.
1. Dans l’administrateur, traitez la commande afin que la quantité de l’article soit mise à jour sur &quot;0&quot;.
1. Assurez-vous que les commandes en arrière-plan ne sont pas autorisées.
1. Sur le storefront, accédez à la même page de produit et sélectionnez les mêmes options : rouge, M.

<u>Résultats attendus</u>:

L’échantillon rouge M a une barre oblique rouge et ne peut pas être sélectionné.

<u>Résultats réels</u>:

L’échantillon rouge M peut être sélectionné.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier ou cliquez sur le lien suivant :

[Téléchargez MDVA-8215\_EE\_2.2.2\_v1.compositeur.patch.](assets/MDVA-8215_EE_2.2.2_v1.composer.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce (toutes les méthodes de déploiement) 2.2.2

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.2.0-2.2.3

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
