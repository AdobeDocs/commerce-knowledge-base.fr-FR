---
title: Échec des paiements par carte de crédit dans un environnement Sandbox
description: Cet article explique pourquoi une carte de crédit de test échoue dans un environnement Sandbox avec les API PayPal.
exl-id: 65fd08e0-eefc-47f3-8964-bef3610e6182
feature: Orders, Payments
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Échec des paiements par carte de crédit dans un environnement Sandbox

Cet article explique pourquoi une carte de crédit de test échoue dans un environnement Sandbox avec les API PayPal.

## Produits et versions concernés


* Adobe Commerce 2.4.0 - 2.4.4 , toutes les options de déploiement, avec [Services de paiement](https://marketplace.magento.com/magento-payment-services.html)

## Problème

Lors de l&#39;utilisation d&#39;une carte de crédit Visa `4111 1111 1111 1111` de PayPal, elle échoue parfois en raison de stratégies de fraude PayPal avec l&#39;erreur suivante :

```bash
Error happened when processing the request. Please try again later.
```

## Cause

Cette erreur s’affiche lorsque PayPal marque un numéro de carte de crédit de test spécifique pour la fraude. Cela se produit car il s’agit d’un numéro de carte de crédit de test utilisé par tous les utilisateurs du monde entier qui effectuent des tests avec les API PayPal.

## Solution

Utilisez une autre carte de crédit de test. Pour générer des cartes de crédit fictives, vous pouvez les utiliser à des fins de test :

1. Accédez à la page [Générateur de carte de crédit](https://developer.paypal.com/developer/creditCardGenerator/) du portail des développeurs PayPal.
1. Connectez-vous au tableau de bord du portail des développeurs PayPal.
1. Générez une carte de crédit de test.
