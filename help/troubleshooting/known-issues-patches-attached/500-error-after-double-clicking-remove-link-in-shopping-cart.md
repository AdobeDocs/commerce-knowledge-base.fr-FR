---
title: '"Erreur 500" après un double clic sur Supprimer le lien dans le panier"'
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.0 lié à l’erreur des clients qui tentent de supprimer deux fois un article du panier (en double-cliquant sur le lien *Supprimer* ou en cliquant dessus dans différents onglets).
exl-id: 927cf681-febf-42cc-8db5-469bcf8f2012
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# &quot;Erreur 500&quot; après avoir double-cliqué sur Supprimer le lien dans le panier

Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.0 lié à l’erreur des clients qui tentent de supprimer deux fois un article du panier (en double-cliquant sur le lien *Supprimer* ou en cliquant dessus dans différents onglets).

## Problème

Lorsque les clients cliquent deux fois sur le lien *Supprimer* dans le panier, en essayant de supprimer un produit du panier, ils obtiennent une page vierge avec le message d’erreur suivant : *&quot;Cette page ne fonctionne pas. HTTP ERROR 500&quot;.* Le même problème se produit si un client ouvre deux onglets de navigateur avec la page du panier et supprime le produit d’abord dans un onglet, puis dans le second.

<u>Étapes à reproduire</u> :

1. Ajoutez un produit au panier sur le storefront.
1. Accédez à la page Panier.
1. Double-cliquez sur le lien Supprimer .

OU

1. Ajoutez un produit au panier sur le storefront.
1. Accédez à la page Panier.
1. Ouvrez un nouvel onglet du navigateur et accédez à la page Panier (même produit).
1. Supprimez le produit du panier.
1. Ouvrez le deuxième onglet et supprimez à nouveau le produit.

<u>Résultat attendu</u> : le produit est supprimé du panier sans erreur.

<u>Résultat réel</u> : le produit est supprimé avec l’erreur : *&quot;Cette page ne fonctionne pas. Message d’erreur HTTP ERROR 500&quot;*.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[Téléchargez MDVA-8623\_EE\_2.2.0\_v1.compositeur.patch.](assets/MDVA-8623_EE_2.2.0_v1.composer.patch.zip)

## Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.2.0

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud 2.2.1 - 2.2.5
* Adobe Commerce On-Premise 2.2.0 - 2.2.5

## Comment appliquer le correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.

## Fichiers attachés
