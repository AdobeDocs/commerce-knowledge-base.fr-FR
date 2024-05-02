---
title: Les nouvelles commandes sont envoyées dans l’archive
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.0 lié aux commandes nouvellement créées qui s’affichent dans l’archive au lieu de la grille Commandes dans Commerce Admin.
exl-id: 37b70d28-0569-44f2-b677-29b2bde0bc5c
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Les nouvelles commandes sont envoyées dans l’archive

Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.0 lié aux commandes nouvellement créées qui s’affichent dans l’archive au lieu de la grille Commandes dans Commerce Admin.

>[!NOTE]
>
>Le problème a été corrigé dans la version 2.2.3 et les versions ultérieures.

## Problème

Lorsque les clients passent des commandes, elles apparaissent dans la grille des commandes archivées au lieu de la grille des commandes standard.

<u>Étapes à reproduire</u>:

1. Ajoutez n’importe quel produit au panier sur le storefront, passez en caisse et passez la commande.
1. Dans l’administrateur de Commerce, accédez à **Ventes** > **Opérations** > **Commande**. Voir l’ordre d’affichage dans la grille.
1. Accédez à **Ventes** > **Archiver** > **Commandes**. Voir le nouvel ordre dans la grille.

<u>Résultats attendus</u>:

La commande est affichée uniquement dans la grille Commandes .

<u>Résultats réels</u>:

L&#39;ordre est affiché dans la grille Commandes et dans la grille d&#39;archivage des commandes.

## Solution

Après avoir appliqué le correctif, les commandes s’affichent dans la grille Ordre comme prévu. Mais vous devez restaurer manuellement dans l’administrateur Commerce ceux qui ont été envoyés pour archivage avant l’application du correctif.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[Téléchargez MDVA-8007\_EE\_2.2.0\_v1.compositeur.patch.](assets/MDVA-8007_EE_2.2.0_v1.composer.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce 2.2.0

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur site, Adobe Commerce sur l’infrastructure cloud 2.2.1 - 2.2.3

## Comment appliquer le correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de soutien.

## Liens utiles dans notre guide d’utilisation

* [Gestion des commandes archivées](https://docs.magento.com/user-guide/sales/order-archive.html)

## Fichiers attachés
