---
title: Modes de paiement non affichés lors du passage en caisse avec plusieurs adresses
description: Cet article explique que la plupart des modes de paiement ne s'affichent pas lors du passage en caisse lorsque plusieurs adresses d'expédition sont spécifiées, car la fonctionnalité n'est implémentée que pour Cybersource.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Modes de paiement non affichés lors du passage en caisse avec plusieurs adresses

Cet article explique que la plupart des modes de paiement ne s&#39;affichent pas lors du passage en caisse lorsque plusieurs adresses d&#39;expédition sont spécifiées, car la fonctionnalité n&#39;est implémentée que pour Cybersource.

## Produits et versions concernés

* Adobe Commerce on-premise 2.x.x
* Adobe Commerce sur l’infrastructure cloud 2.x.x

>[!NOTE]
>
>L’intégration de base des paiements Adobe Commerce Cybersource est obsolète depuis la version 2.3.3 et sera complètement supprimée dans la version 2.4.0. Utilisez plutôt l’extension [officielle](https://marketplace.magento.com/cybersource-global-payment-management.html) de Marketplace.

## Problème

<u>Conditions préalables</u> : dans Commerce Admin, activez et configurez les méthodes de paiement PayPal et Cybersource, et activez Multishipping pour votre boutique.

<u>Procédure à suivre </u> :

1. Sur le storefront, ajoutez plusieurs produits au panier.
1. Accédez à la page du panier.
1. Cliquez sur **Extraire avec plusieurs adresses**.
1. Connectez-vous ou créez un compte.
1. Répartissez les produits entre les adresses de la page Adresse de livraison .
1. Cliquez sur **Accéder aux informations d’expédition**.
1. Sélectionnez les modes d&#39;expédition pour chaque expédition.
1. Cliquez sur **Continuer vers les informations de facturation**.

<u>Résultat attendu</u> : PayPal et Cybersource sont disponibles comme options de paiement.

<u>Résultat réel</u> : seule Cybersource apparaît comme option de paiement disponible.

## Cause

Actuellement, Cybersource est la seule méthode de paiement en direct prise en charge pour le passage en caisse multiexpédition, à partir de la version 2.2.4. La prise en charge du multienvoi sera probablement créée pour chaque mode de paiement un par un. Aucune date exacte ni aucun numéro de version ne peuvent être fournis pour le moment.
