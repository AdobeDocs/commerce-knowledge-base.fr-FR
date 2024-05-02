---
title: Correctif du problème de paiement Amazon dans Adobe Commerce 2.3.5-p1
description: Ce correctif résout le problème en raison duquel il est impossible de modifier un mode de paiement à l’étape "Révision et paiements" du widget des paiements, lors de l’extraction avec la paye Amazon dans Adobe Commerce.
exl-id: a241f67f-019c-4ff2-a5ad-e7dc71639768
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Correctif du problème de paiement Amazon dans Adobe Commerce 2.3.5-p1

Ce correctif résout le problème en raison duquel il est impossible de modifier un mode de paiement à l’étape &quot;Révision et paiements&quot; du widget des paiements, lors de l’extraction avec la paye Amazon dans Adobe Commerce.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud version 2.3.5-p1
* Adobe Commerce on-premise version 2.3.5-p1

## Problème

Lorsqu’un acheteur passe en caisse avec le paiement Amazon, se connecte, passe à l’étape de paiement et tente de modifier sa carte de crédit de paiement à partir du widget de paiements, un message d’erreur s’affiche. Le passage en caisse ne peut pas être terminé si l’acheteur ignore l’erreur et passe en caisse.

Pour résoudre ce problème et supprimer l’erreur, nous avons créé une [correctif](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip).

<u>Étapes à reproduire</u>:

1. Commencez le passage en caisse avec Amazon Pay.
1. Connectez-vous en tant que client Amazon Pay.
1. Sélectionnez le mode de livraison et passez à l’étape de paiement.
1. Essayez de changer de carte de crédit.

<u>Résultat attendu</u>: une autre carte de crédit est sélectionnée comme mode de paiement sans erreur.

<u>Résultat réel</u>: le message d’erreur s’affiche : *&quot;Veuillez contacter ce marchand pour obtenir de l’aide pour terminer votre commande.&quot;*

## Solution

[Appliquer le correctif](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip) ci-dessous

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[Télécharger BUNDLE-2554\_EE\_2.3.5-p1.compositeur.patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud version 2.3.5-p1
* Adobe Commerce on-premise version 2.3.5-p1

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud version 2.3.5
* Adobe Commerce On-Premise version 2.3.5

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
