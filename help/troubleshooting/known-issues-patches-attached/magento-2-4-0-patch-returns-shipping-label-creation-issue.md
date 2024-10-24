---
title: 'Correctif Adobe Commerce 2.4.0 : renvoie le problème de création des libellés d’expédition'
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.4.0 en cas de problème d’impression d’une étiquette d’expédition pour les retours des clients.
exl-id: f78f8d7e-29e9-4d6c-83f6-cd5afa1d7d9c
feature: B2B, Orders, Returns, Communications, Shipping/Delivery
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Correctif Adobe Commerce 2.4.0 : renvoie un problème de création d’étiquettes d’expédition

Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.4.0 en cas de problème d’impression d’une étiquette d’expédition pour les retours des clients.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problème

<u>Étapes à reproduire :</u>

1. Effectuez une commande avec l’une des méthodes principales de livraison suivantes : FedEx, DHL, UPS et USPS.
1. Créez et autorisez des retours pour cette commande.
1. Ouvrez une page **Informations sur le retour** autorisée et cliquez sur le bouton **Créer une étiquette d’expédition**.
1. Sélectionnez le mode de livraison, ajoutez un produit à un package et cliquez sur Enregistrer.

<u>Résultat attendu :</u>

Une étiquette de livraison a été créée avec succès et un message s’affiche : *Vous avez créé une étiquette de livraison.*

<u>Résultat réel :</u>

La page **Informations sur le retour** est endommagée et un message d’erreur s’affiche sur la page Informations sur le retour : *des modifications d’informations générales ont été apportées à cette section qui n’ont pas été enregistrées. Cet onglet contient des données non valides*.

## Solution

Appliquez [patch](assets/MC-35984-2.4.0-CE-composer.patch.zip) fourni dans cet article.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[MC-35984-2.4.0-CE-compositeur.patch](assets/MC-35984-2.4.0-CE-composer.patch.zip)

Le correctif peut également être téléchargé dans les formats `.git` et `.composer` de la page [Téléchargements Adobe Commerce](https://magento.com/tech-resources/download), sous **Correctifs** dans le volet de navigation de la colonne de gauche. Recherchez le correctif MC-35984.

## Comment appliquer le correctif

Pour obtenir des instructions, reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre page de connaissances sur la prise en charge.

## Lectures connexes dans notre base de connaissances de support :

* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur le storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton &quot;Ajouter des sélections à mon panier&quot; ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les méthodes de paiement du Braintree ne s’affichent pas dans le passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [L’administrateur d’Adobe Commerce 2.4.0 B2B ne peut pas ajouter de produit configurable pour le devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur d’affichage des commandes](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
