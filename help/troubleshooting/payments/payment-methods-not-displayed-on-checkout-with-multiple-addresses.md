---
title: Modes de paiement non affichés lors de l’extraction avec plusieurs adresses
description: Cet article explique que la plupart des méthodes de paiement ne s’affichent pas lors du passage en caisse lorsque plusieurs adresses de livraison sont spécifiées, car la fonctionnalité est uniquement mise en oeuvre pour Cybersource.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Modes de paiement non affichés lors de l’extraction avec plusieurs adresses

Cet article explique que la plupart des méthodes de paiement ne s’affichent pas lors du passage en caisse lorsque plusieurs adresses de livraison sont spécifiées, car la fonctionnalité est uniquement mise en oeuvre pour Cybersource.

## Produits et versions concernés

* Adobe Commerce On-Premise 2.x.x
* Adobe Commerce sur l’infrastructure cloud 2.x.x

>[!NOTE]
>
>L’intégration de paiement Adobe Commerce Cybersource principale est obsolète depuis la version 2.3.3 et sera complètement supprimée de la version 2.4.0. Utilisez plutôt l’ [extension officielle](https://marketplace.magento.com/cybersource-global-payment-management.html) de Marketplace.

## Problème

<u>Conditions préalables</u> : dans l’administrateur Commerce, activez et configurez les méthodes de paiement PayPal et Cybersource, et activez la multidiffusion pour votre boutique.

<u>Étapes à reproduire</u> :

1. Sur le storefront, ajoutez plusieurs produits au panier.
1. Accédez à la page du panier.
1. Cliquez sur **Extraire avec plusieurs adresses**.
1. Connectez-vous ou créez un compte.
1. Partage des produits entre les adresses sur la page Ship to Multiple Addresses.
1. Cliquez sur **Accéder à Informations d’expédition**.
1. Choisissez les méthodes de livraison pour chaque envoi.
1. Cliquez sur **Continuer vers les informations de facturation**.

<u>Résultat attendu</u> : PayPal et Cybersource sont disponibles en tant qu’options de paiement.

<u>Résultat réel</u> : seule la cybersource apparaît comme option de paiement disponible.

## Cause

Actuellement, Cybersource est le seul mode de paiement en direct pris en charge pour le paiement multiexpédition, à partir de la version 2.2.4. La prise en charge de la multilivraison sera probablement générée une par une pour chaque mode de paiement. Aucune date ou numéro de version exact ne peut être fournie pour le moment.
