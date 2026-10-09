---
title: 'Adobe Commerce 2.4.2 : Braintree Venmo ne fonctionne pas'
description: Cet article décrit un problème Adobe Commerce 2.4.2 connu en raison duquel les commandes ne sont pas générées lors de l’utilisation de Braintree Venmo lors du passage en caisse. Aucune résolution n’est disponible pour le moment.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
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
