---
title: "Adobe Commerce 2.4.4 : impossible de créer des factures partielles"
description: Cet article fournit un correctif pour le problème où les utilisateurs ne sont pas en mesure de créer des factures partielles lors de l’utilisation d’Apple Pay ou de Google Pay through Braintree comme méthode de paiement.
exl-id: bf78cc07-9dc7-4eb8-bfdf-57ea5131effb
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Adobe Commerce 2.4.4 : impossible de créer des factures partielles

Cet article fournit un correctif pour le problème où les utilisateurs ne sont pas en mesure de créer des factures partielles lors de l’utilisation d’Apple Pay ou de Google Pay through Braintree comme méthode de paiement.

## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

## Problème

Lors de l’utilisation des méthodes de paiement Apple Pay ou Google Pay, les utilisateurs reçoivent l’erreur &quot;*La commande &quot;vault_capture&quot; n’existe pas. Vérifiez la commande et réessayez.*&quot; lors de la création de factures partielles.

<u>Étapes à reproduire</u> :

1. Ouvrez votre site web Adobe Commerce.
1. Ajoutez un produit simple au panier (quantité 2).
1. Choisissez **Paiement Apple** ou **Paiement Google** comme mode de paiement dans le panier.
1. Placez la commande.
1. Ouvrez les détails de la commande à partir du serveur principal.
1. Créez une facture partielle.
1. Créez une autre facture pour le montant restant.

<u>Résultats attendus</u> :

Des factures partielles sont créées.

<u>Résultats réels</u> :

La première facture partielle est créée. Lors de la création de la deuxième facture partielle, les utilisateurs reçoivent l’erreur suivante : *La commande ‘vault_capture’ n’existe pas. Vérifiez la commande et réessayez*.

## Cause

Adobe Commerce enregistre les détails de la carte de crédit dans le coffre pour créer des factures partielles. Actuellement, il n’existe aucune fonctionnalité permettant de valider Apple Pay et Google Pay.

## Solution

Pour résoudre ce problème, appliquez le correctif suivant :

[Braintree_disabled_partiel_capture_for_applepay_googlepay.zip](assets/braintree-disabled-partial-capture-for-applepay-googlepay.zip)

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.
