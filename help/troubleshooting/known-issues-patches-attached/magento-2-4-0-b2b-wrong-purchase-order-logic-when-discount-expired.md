---
title: "Adobe Commerce 2.4.0 B2B : logique de bon de commande erronée lorsque la remise a expiré"
description: Cet article fournit un correctif pour le problème connu d’une remise de bon de commande (PO) qui n’est pas appliquée dans Adobe Commerce 2.4.0 B2B. Si le bon de commande a été placé avec un code de remise qui a expiré pendant que le bon de commande était dans le processus de validation, la commande approuvée ne reflète pas la remise.
exl-id: 3ef41655-c31e-4e9c-8985-fa1b4fd53170
feature: B2B, Orders, Payments, Personalization, Purchase Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B : logique de bon de commande erronée lorsque la remise a expiré

Cet article fournit un correctif pour le problème connu d’une remise de bon de commande (PO) qui n’est pas appliquée dans Adobe Commerce 2.4.0 B2B. Si le bon de commande a été placé avec un code de remise qui a expiré pendant que le bon de commande était dans le processus de validation, la commande approuvée ne reflète pas la remise.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problème

<u>Conditions préalables</u> : création d’un coupon de réduction et des règles de validation qui empêchent le traitement automatique des commandes.

<u>Étapes à reproduire :</u>

1. Placez un bon de commande avec une remise appliquée.
1. Désactivez le coupon de réduction.
1. Validez le bon de commande en tant que responsable.
1. Vérifiez l&#39;ordre créé à la suite de cette opération.

<u>Résultat attendu :</u>

La commande est créée avec un total actualisé.

<u>Résultat réel :</u>

La commande est créée pour le montant total.

## Solution

Appliquez le correctif fourni dans cet article.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[B2B-709-composer.patch](assets/B2B-709-composer.patch.zip)

Le correctif peut également être téléchargé dans les formats `.git` et `.composer` de la page [Téléchargements Adobe Commerce](https://magento.com/tech-resources/download), sous **Correctifs** dans le volet de navigation de la colonne de gauche. Recherchez le correctif XXX.

## Comment appliquer le correctif

Pour obtenir des instructions, reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.
