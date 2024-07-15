---
title: "Problème connu d’Adobe Commerce 2.4.1 : erreur apparaissant lors du passage en caisse avec le Braintree PayPal"
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.1, en raison duquel un message d’erreur s’affiche et disparaît à l’étape Facturation du passage en caisse si le paiement du Braintree PayPal est utilisé et que plusieurs adresses sont sélectionnées.
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Problème connu d’Adobe Commerce 2.4.1 : erreur apparaissant lors du passage en caisse avec le Braintree PayPal

Cet article décrit un problème connu d’Adobe Commerce 2.4.1, en raison duquel un message d’erreur s’affiche et disparaît à l’étape Facturation du passage en caisse si le paiement du Braintree PayPal est utilisé et que plusieurs adresses sont sélectionnées.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.1
* Adobe Commerce on-premise 2.4.1

## Problème

Un message d’erreur s’affiche et disparaît à l’étape Facturation du passage en caisse si le paiement du Braintree PayPal est utilisé et que l’envoi d’adresses multiples est sélectionné.

<u>Étapes à reproduire :</u>

1. Sur le storefront, connectez-vous en tant que client (éventuellement un passage en caisse invité, s’il est activé dans Admin).
1. Ajoutez un produit au panier.
1. Cliquez sur pour ouvrir l’aperçu du panier.
1. Cliquez sur **Afficher et modifier le panier**.
1. Sur la page Panier, cliquez sur **Extraire avec plusieurs adresses**.
1. Cliquez sur **Accéder aux Informations d’expédition** et indiquez les adresses.
1. Cliquez sur **Continuer vers les informations de facturation**.
1. Sélectionnez **Braintree PayPal** et cliquez sur le bouton **PayPal** .
1. Dans la fenêtre contextuelle, cliquez sur **Accepter et payer**.

<u>Résultat attendu :</u>

La commande est passée sans erreur.

<u>Résultat réel :</u>

La commande est placée, mais avec une erreur. Le *paiement PayPal n&#39;a pas pu être initialisé. Veuillez contacter le propriétaire du magasin*.  s’affiche pendant une seconde et disparaît.

## Correction

Comme le placement de la commande n’est pas bloqué, il n’est pas nécessaire d’effectuer des étapes de contournement.
