---
title: 'Adobe Commerce 2.4.2 : Braintree Venmo ne fonctionne pas'
description: Cet article décrit un problème Adobe Commerce 2.4.2 connu en raison duquel les commandes ne sont pas générées lors de l’utilisation de Braintree Venmo lors du passage en caisse. Aucune résolution n’est disponible pour le moment.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 : Braintree Venmo ne fonctionne pas

Cet article décrit un problème Adobe Commerce 2.4.2 connu en raison duquel les commandes ne sont pas générées lors de l’utilisation de Braintree Venmo lors du passage en caisse. Aucune résolution n’est disponible pour le moment.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

## Problème

<u>Condition préalable</u> :

Activez le paiement Venmo dans la configuration de Braintree.

<u>Procédure à suivre </u> :

1. Sur la vitrine, ajoutez n’importe quel article dans le panier.
1. Passez à **Passage en caisse**.
1. Sélectionnez le mode d&#39;expédition approprié.
1. Sélectionnez **Venmo** comme mode de paiement.
1. Cliquez sur **Payer avec Venmo**.
1. Cliquez sur **Passer une commande**.

<u>Résultats réels</u> :

La commande n’est pas créée dans le code Adobe Commerce après la redirection du client vers le magasin à partir de l’application Venmo et aucun message d’erreur ne s’affiche. La commande est créée dans Braintree.

<u>Résultats attendus</u> :

La commande est créée dans Adobe Commerce après la redirection du client vers le magasin à partir de l’application Venmo et la commande est créée dans Braintree, comme prévu.

## Solution

Aucune résolution n’est disponible pour le moment.
