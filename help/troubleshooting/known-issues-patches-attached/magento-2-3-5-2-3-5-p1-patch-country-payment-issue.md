---
title: 'Correctif Adobe Commerce 2.3.5, 2.3.5-p1 : problème de paiement du pays'
description: Ce correctif résout un problème dans Adobe Commerce en raison duquel le workflow de paiement de vitrine n’affichait aucun mode de paiement activé pour des pays spécifiques, à l’exception de Klarna et Amazon Pay.
exl-id: e205e35e-9ffe-4826-b951-3a3caf1e0621
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Correctif Adobe Commerce 2.3.5, 2.3.5-p1 : problème de paiement du pays

Ce correctif résout un problème dans Adobe Commerce en raison duquel le workflow de paiement de vitrine n’affichait aucun mode de paiement activé pour des pays spécifiques, à l’exception de Klarna et Amazon Pay.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.3.5 et 2.3.5-p1
* Adobe Commerce on-premise 2.3.5 et 2.3.5-p1

## Problème

Lorsqu’un pays est affecté à un magasin et qu’un autre paiement est affecté à un autre pays, et que l’un de ces pays et modes de paiement est sélectionné, les boutons Mode de paiement et Passer une commande ne sont pas visibles.

L’actualisation d’une page web est une solution au problème.

Pour résoudre ce problème et supprimer l’erreur, nous avons créé une [correctif](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip).

<u>Conditions préalables</u>:

* Un produit simple est créé.
* **Commande d’archivage/de paiement** est activé uniquement pour des pays spécifiques (à l’adresse **Magasin** > **Configuration** > **Ventes** > **Méthodes de paiement**).

* Exemple : paiement depuis les pays applicables = pays spécifiques
* Exemple : paiement de pays spécifiques = Royaume-Uni

<u>Étapes à reproduire</u>:

1. Allez sur le storefront en tant qu&#39;invité.
1. Ajoutez un produit simple au panier.
1. Accédez à Passage en caisse.
1. Remplissez le formulaire avec des données valides.

   * Pays = *États-Unis*

1. Sélectionnez le taux d’expédition et cliquez sur **Suivant**.

   * L’étape de paiement est ouverte.
   * Il n’y a aucun paiement disponible.
   * Message : **Aucun mode de paiement disponible.**
   * Il n’y a pas de **Passer commande** bouton .

1. Revenez au **Étape d’expédition** et modifiez la valeur en :

   * Pays = *Royaume-Uni*

1. Sélectionnez le taux d’expédition et cliquez sur **Suivant**.

<u>Résultat attendu</u>:

L’étape Paiement s’ouvre.

* **Espèces à la livraison** apparaît.
* **Commande d’archivage/de paiement** apparaît.
* La variable **Passer commande** s’affiche.

<u>Résultat réel</u>:

L’étape Paiement s’ouvre.

* Il n’y a aucun paiement disponible.
* Message : *Aucun mode de paiement disponible.*
* Il n’y a pas de **Passer commande** bouton .

## Solution

[Appliquer le correctif](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip) ci-dessous

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier ou cliquez sur le lien suivant :

[Télécharger BUNDLE-2546\_EE\_2.3.5-p1.compositeur.patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.3.5 et 2.3.5-p1
* Adobe Commerce on-premise 2.3.5 et 2.3.5-p1

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce versions 2.3.4-p2 - 2.2.6

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
