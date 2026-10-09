---
title: 'Adobe Commerce 2.4.2 B2B : la remise reste un changement de mode de paiement'
description: Cet article décrit un problème B2B Adobe Commerce 2.4.2 connu où une remise liée au mode de paiement persiste après un changement de mode de paiement lors du passage en caisse. Aucune résolution n’est disponible pour le moment.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%
---
# Adobe Commerce 2.4.2 B2B : la remise reste un changement de mode de paiement

Cet article décrit un problème B2B Adobe Commerce 2.4.2 connu où une remise liée au mode de paiement persiste après un changement de mode de paiement lors du passage en caisse. Aucune résolution n’est disponible pour le moment.

## Produits et versions concernés

* Adobe Commerce 2.4.2
* Adobe Commerce sur les infrastructures cloud 2.4.2
* B2B pour Adobe Commerce 1.3.1


## Problème

<u>Procédure à suivre </u> :

1. Créez un panier **Règle de prix** lié à un mode de paiement (exemple : les utilisateurs de Paypal bénéficient d’une remise de 20 %).
1. Créez un bon de commande et sélectionnez Paypal comme mode de paiement. La remise est appliquée.
1. Le bon de commande est approuvé.
1. Accédez à la page de paiement pour terminer la commande.
1. Sélectionnez un autre mode de paiement.

<u>Résultats réels</u> :

L&#39;escompte du mode de paiement reste appliqué au total de la commande.  Aucun message d’erreur ne s’affiche.Le propriétaire du magasin pourra constater cette erreur en vérifiant l’historique des commandes.

<u>Résultats attendus</u> :The escompte sur le mode de paiement est supprimé du total de la commande, comme prévu.

## Solution

Aucune résolution n’est disponible pour le moment.
