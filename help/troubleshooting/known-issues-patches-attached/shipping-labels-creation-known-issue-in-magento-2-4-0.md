---
title: Problème connu de création des libellés d’expédition dans Adobe Commerce 2.4.0
description: Cet article fournit un correctif pour un problème connu d’Adobe Commerce 2.4.0, dans lequel une étiquette de livraison ne peut pas être créée.
exl-id: 722689d9-0c90-4a9d-8449-e93c6585b7c3
feature: Orders, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Problème connu de création des libellés d’expédition dans Adobe Commerce 2.4.0

Cet article fournit un correctif pour un problème connu d’Adobe Commerce 2.4.0, dans lequel une étiquette de livraison ne peut pas être créée.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

<u>Conditions préalables</u> : créez une commande à l’aide de la méthode d’expédition FedEx, DHL, UPS ou USPS.

### Scénario 1 : créer un libellé lors de l’ajout d’une expédition

<u>Étapes à reproduire :</u>

1. Ouvrez la commande passée dans l’administrateur, sous **Sales** > **Commandes**.
1. Cliquez sur le bouton **Ship** . La page **New Shipment** s’ouvre.

<u>Résultat attendu :</u>

La case à cocher **Créer un libellé d’expédition** s’affiche au bas de la page.

<u>Résultat réel :</u>

La case à cocher **Créer un libellé d’expédition** ne s’affiche pas.

### Scénario 2 : créer un libellé pour une expédition existante

<u>Étapes à reproduire :</u>

1. Ouvrez la commande passée dans l’administrateur, sous **Sales** > **Commandes**.
1. Cliquez sur le bouton **Ship** . La page **New Shipment** s’ouvre.
1. Cliquez sur le bouton **Submit Shipment** . Une expédition est créée.
1. Ouvrez l&#39;expédition nouvellement créée.
1. Cliquez sur le bouton **Créer un libellé d’expédition** . La boîte de dialogue **Créer des packages** s’ouvre.

<u>Résultat attendu :</u>

Le bouton **Ajouter des produits au module** de la fenêtre modale **Créer des modules** affiche les champs avec des éléments de commande.

<u>Résultat réel :</u>

La fenêtre modale **Créer des packages** ne s’affiche pas correctement. Il n’est pas possible d’ajouter des éléments de commande à l’envoi.

## Solution

Appliquez le correctif fourni dans cet article.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[MC-35514-2.4.0-CE-compositeur-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

Le correctif peut également être téléchargé dans les formats `.git` et `.composer` de la page [Téléchargements Adobe Commerce](https://magento.com/tech-resources/download), sous **Correctifs** dans le volet de navigation de la colonne de gauche. Recherchez le correctif MC-35514.

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud version 2.4.0
* Adobe Commerce On-Premise version 2.4.0

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
