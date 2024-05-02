---
title: "Adobe Commerce 2.4.2 : le paiement de Venmo Braintree ne fonctionne pas"
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.2, en raison duquel les commandes ne sont pas générées lors de l’utilisation de Venmo Braintree lors du passage en caisse. Aucune résolution n’est disponible pour le moment.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 : le paiement de Venmo Braintree ne fonctionne pas

Cet article décrit un problème connu d’Adobe Commerce 2.4.2, en raison duquel les commandes ne sont pas générées lors de l’utilisation de Venmo Braintree lors du passage en caisse. Aucune résolution n’est disponible pour le moment.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

## Problème

<u>Condition préalable</u> :

Activez le paiement Venmo dans la configuration du Braintree.

<u>Étapes à reproduire</u> :

1. Sur le storefront, ajoutez n’importe quel article au panier.
1. Passez à **Passage en caisse**.
1. Sélectionnez le mode de livraison approprié.
1. Sélectionner **Venmo** comme mode de paiement.
1. Cliquez sur **Payer avec Venmo**.
1. Cliquez sur **Passer commande**.

<u>Résultats réels</u>:

La commande n’est pas créée dans le code Adobe Commerce une fois que le client a été redirigé vers la boutique à partir de l’application Venmo et qu’aucun message d’erreur ne s’affiche. La commande est créée dans Braintree.

<u>Résultats attendus</u>:

La commande est créée dans Adobe Commerce une fois que le client est redirigé vers la boutique à partir de l’application Venmo et que la commande est créée dans Braintree, comme prévu.

## Solution

Aucune résolution n’est disponible pour le moment.
