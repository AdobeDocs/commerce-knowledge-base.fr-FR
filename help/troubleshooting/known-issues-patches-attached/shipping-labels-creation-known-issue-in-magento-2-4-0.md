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

<u>Conditions préalables</u>: créez une commande à l’aide de la méthode d’expédition FedEx, DHL, UPS ou USPS.

### Scénario 1 : créer un libellé lors de l’ajout d’une expédition

<u>Étapes à reproduire :</u>

1. Ouvrez la commande passée dans l’Admin, sous **Ventes** > **Commandes**.
1. Cliquez sur le bouton **Ship** bouton . La variable **Nouvel envoi** s’ouvre.

<u>Résultat attendu :</u>

La variable **Créer une étiquette d’expédition** s’affiche en bas de la page.

<u>Résultat réel :</u>

La variable **Créer une étiquette d’expédition** n’est pas affichée.

### Scénario 2 : créer un libellé pour une expédition existante

<u>Étapes à reproduire :</u>

1. Ouvrez la commande passée dans l’Admin, sous **Ventes** > **Commandes**.
1. Cliquez sur le bouton **Ship** bouton . La variable **Nouvel envoi** s’ouvre.
1. Cliquez sur le bouton **Envoyer l’envoi** bouton . Une expédition est créée.
1. Ouvrez l&#39;expédition nouvellement créée.
1. Cliquez sur le bouton **Créer une étiquette d’expédition** bouton . La variable **Création de modules** s’ouvre.

<u>Résultat attendu :</u>

La variable **Ajout de produits au module** sur le bouton **Création de modules** fenêtre modale affiche les champs avec des éléments de commande.

<u>Résultat réel :</u>

La variable **Création de modules** fenêtre modale ne s’affiche pas correctement, il n’est pas possible d’ajouter des éléments de commande à l’envoi.

## Solution

Appliquez le correctif fourni dans cet article.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[MC-35514-2.4.0-CE-compositeur-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

Le correctif peut également être téléchargé dans les deux `.git` et `.composer`, formats sur [Téléchargements Adobe Commerce](https://magento.com/tech-resources/download) page, sous **Correctifs** dans la navigation en colonne de gauche. Recherchez le correctif MC-35514.

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud version 2.4.0
* Adobe Commerce On-Premise version 2.4.0

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
