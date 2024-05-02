---
title: "Problème connu d’Adobe Commerce 2.3.7-p1 : total des commandes obsolète pour PayPal"
description: "Cet article fournit un correctif pour un problème connu dans Adobe Commerce 2.3.7-p1 : lorsque vous utilisez le paiement PayPal plus d’une fois que les clients reçoivent le produit précédemment commandé dans le panier, au lieu du nouveau qu’ils tentent de commander."
exl-id: ceb8f7ad-0cf7-4d42-aded-25d1dd947f5b
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Problème connu d’Adobe Commerce 2.3.7-p1 : total des commandes obsolète pour PayPal

Cet article fournit un correctif pour un problème connu dans Adobe Commerce 2.3.7-p1 : lorsque vous utilisez le paiement PayPal plus d’une fois que les clients reçoivent le produit précédemment commandé dans le panier, au lieu du nouveau qu’ils tentent de commander.
Vous pouvez télécharger le correctif à partir de cet article et il est également disponible via l’outil de correctifs de qualité (QPT).

## Versions affectées

* Adobe Commerce (toutes les options de déploiement) 2.3.7-p1
* Magento Open Source 2.3.7-p1

## Problème

Lorsque vous passez une commande en utilisant le mode de paiement paiement paiement paiement paiement paiement paiement paiement express de PayPal, le produit précédemment commandé est ajouté à la commande au lieu du produit réel.

<u>Étapes à reproduire :</u>

1. Au niveau du magasin, ajoutez n’importe quel produit au panier (produit A, prix de 50 $).
1. Cliquez sur le lien du panier pour ouvrir le panier.
1. Cliquez sur le bouton **Passage en caisse PayPal** bouton .
1. Utilisez vos informations d’identification PayPal pour vous connecter à PayPal et envoyer le paiement.
1. Terminez le placement de la commande côté magasin.
1. Revenez au catalogue et ajoutez un autre produit (produit B, prix 100 $) au panier.
1. Cliquez sur le lien du panier pour ouvrir le panier.
1. Cliquez sur le bouton **Passage en caisse PayPal** bouton .

<u>Résultat réel :</u>

Le prix du produit dans le panier est de 50 $ au lieu de 100 $.<br/>
Côté magasin, la commande contient le produit A au lieu du produit B.

<u>Résultat attendu :</u>

Le produit B est ajouté à la commande.

## Solution

Appliquez le correctif fourni dans cet article.

## Correctif

Utilisez le lien suivant pour télécharger un fichier .zip contenant le correctif : [MC42674-compositeur.patch.zip](assets/MC42674-composer.patch.zip).

### Versions Adobe Commerce compatibles

* Adobe Commerce (toutes les options de déploiement) 2.3.7-p1

## Comment appliquer les correctifs

1. Décompressez le fichier .zip téléchargé.
1. Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour plus d’informations.
