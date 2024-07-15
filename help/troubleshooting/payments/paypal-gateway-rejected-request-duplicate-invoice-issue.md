---
title: Demande de rejet de la passerelle PayPal - problème de facture en double
description: Cet article fournit un correctif pour la demande de rejet de la passerelle PayPal - problème de doublon de facture.
exl-id: b6c4ede1-97a5-4db3-9b05-ab979cf809b3
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Demande de rejet de la passerelle PayPal - problème de facture en double

Cet article fournit un correctif pour la demande de rejet de la passerelle PayPal - problème de doublon de facture.

Lors de l’envoi du paiement, les clients peuvent voir une erreur pour une facture en double :

>La passerelle PayPal a rejeté la demande. Le paiement a déjà été effectué pour cet InvoiceID (\#10412: Dupliquer la facture)

Le problème se produit lorsque des factures avec les mêmes ID sont envoyées à PayPal plusieurs fois.

Pour résoudre le problème, autorisez plusieurs paiements par identifiant de facture dans les préférences de réception des paiements de PayPal. Lorsqu’elle est modifiée, PayPal accepte les paiements sans message d’erreur, même pour les factures avec des ID en double.

## Versions affectées

* Adobe Commerce sur site, toutes versions
* Adobe Commerce sur l’infrastructure cloud, toutes les versions

## Problème

Lors de l’envoi du paiement, les clients voient le message d’erreur :

```
... main.CRITICAL: Exception message: PayPal gateway has rejected request. Payment has already been made for this InvoiceID (#10412: Duplicate invoice).
```

PayPal ne peut pas traiter le paiement et terminer la commande.

## Cause

Le message d’erreur s’affiche lorsque des factures avec le même ID sont envoyées à PayPal plusieurs fois.

Cela peut se produire lors de l’utilisation des mêmes informations d’identification sur plusieurs sites Adobe Commerce (même dans les environnements local et intermédiaire). Voici quelques scénarios particuliers :

* Plusieurs magasins envoient des factures à PayPal et utilisent les mêmes identifiants de facture
* Un nouveau magasin envoie une facture avec un identifiant qui a déjà été envoyé par un ancien magasin.

Par défaut, PayPal n&#39;autorise pas le traitement de la même facture à deux reprises.

## Solution

Modifiez votre profil PayPal afin de permettre plusieurs paiements par identifiant de facture. Vous devez effectuer ces modifications via PayPal.

1. Connectez-vous à votre compte à l’adresse [https://www.paypal.com](https://www.paypal.com/).
1. Cliquez sur **Profil** > **Profil et paramètres** (coin supérieur droit).
1. Accédez à **Mes outils de vente**.
1. Accédez à **Obtenir un paiement et gérer mon risque** > **Bloquer les paiements** et cliquez sur **Mettre à jour**.
1. **Préférences de vente**, cliquez sur **Préférences de réception des paiements**.
1. Sous **Bloquer les paiements accidentels**, sélectionnez **Non, autorisez plusieurs paiements par identifiant de facture**.    ![paypal_allow_multiple_payments_per_facture_id.png{1](assets/paypal_allow_multiple_payments_per_invoice_id.png)
1. Faites défiler l’écran jusqu’au bas de l’écran et cliquez sur **Enregistrer**.

## Informations supplémentaires

* [Bloquez les paiements accidentels](https://developer.paypal.com/docs/admin/setup-account/#block-accidental-payments) sur les documents de développement PayPal.
* Paiements PayPal dans notre guide d’utilisation :
   * [Passage en caisse express PayPal](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html)
   * [Autres solutions PayPal](/docs/commerce-admin/stores-sales/payments/paypal/paypal.html)
* Dans notre documentation destinée aux développeurs :
   * [Configuration des méthodes de paiement PayPal pour Adobe Commerce sur l’infrastructure cloud](/docs/commerce-cloud-service/user-guide/configure-store/paypal.html)
   * [Intégrations de paiements](https://developer.adobe.com/commerce/php/development/payments-integrations/)
