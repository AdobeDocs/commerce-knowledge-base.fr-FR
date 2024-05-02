---
title: "Adobe Commerce 2.4.0, 2.4.1 : Activer la facture partielle Venmo Braintree"
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.0 et 2.4.1, où une facture partielle n’est pas disponible pour les commandes passées à l’aide de Braintree via Venmo.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0, 2.4.1 : activation de la facture partielle Venmo Braintree

Cet article décrit un problème connu d’Adobe Commerce 2.4.0 et 2.4.1, où une facture partielle n’est pas disponible pour les commandes passées à l’aide de Braintree via Venmo.

## Produits et versions concernés

* Adobe Commerce sur site 2.4.0 et 2.4.1
* Adobe Commerce sur l’infrastructure cloud 2.4.0 et 2.4.1

## Problème

<u>Conditions préalables :</u>

Dans la configuration du mode de paiement du Braintree, définissez **Activation de Venmo via Braintree** = *Oui* avec **Action de paiement** = *Autorisation*; **Activation de Vault pour les paiements par carte** = *Non*.

<u>Étapes à reproduire :</u>

1. Créez une commande pour plusieurs produits, en utilisant Venmo (Braintree) comme méthode de paiement.
1. Ouvrez la commande dans l’administrateur Commerce.
1. Créez une facture pour l’un des produits commandés.
1. Essayez de créer une facture pour les autres produits commandés.

<u>Résultat attendu :</u>

Facture créée.

<u>Résultat réel :</u>

Le message d&#39;erreur suivant s&#39;affiche : *La commande &quot;vault\_capture&quot; n’existe pas. Vérifiez la commande et réessayez.*

## Solution

Capturez le montant entier lors de la création de factures pour les commandes passées via Braintree via Venmo.
