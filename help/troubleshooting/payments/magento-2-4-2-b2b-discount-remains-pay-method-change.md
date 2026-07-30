---
title: 'Adobe Commerce 2.4.2 B2B : la remise reste un changement de mode de paiement'
description: Cet article décrit un problème B2B Adobe Commerce 2.4.2 connu où une remise liée au mode de paiement persiste après un changement de mode de paiement lors du passage en caisse. Aucune résolution n’est disponible pour le moment.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
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
