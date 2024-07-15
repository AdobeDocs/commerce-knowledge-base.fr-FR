---
title: Plus de produits ont été supprimés qu’ils n’ont été lancés lors d’une suppression en masse dans Admin
description: Cet article fournit un correctif pour l’Adobe connu С commerce sur l’infrastructure cloud 2.2.3 lié au fait que des enregistrements non sélectionnés n’aient pas été supprimés lorsqu’une suppression en masse est effectuée dans une grille dans l’administrateur Commerce.
exl-id: 0bfdc84e-0292-4702-a20e-bdbe67c111a2
feature: Admin Workspace, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Plus de produits ont été supprimés qu’ils n’ont été lancés lors d’une suppression en masse dans Admin

Cet article fournit un correctif pour l’Adobe connu С commerce sur l’infrastructure cloud 2.2.3 lié au fait que des enregistrements non sélectionnés n’aient pas été supprimés lorsqu’une suppression en masse est effectuée dans une grille dans l’administrateur Commerce.

## Problème

Dans l&#39;Admin, si vous sélectionnez les enregistrements de client ou de client à supprimer, filtrez la grille, puis sélectionnez l&#39;action **Supprimer**, tous les enregistrements sont supprimés.

<u>Étapes à reproduire</u> :

1. Accédez à **Catalogue** > **Produits** dans l’administrateur.
1. Sélectionnez un ou plusieurs produits.
1. Sélectionnez Supprimer dans le menu déroulant Actions .

<u>Résultats attendus</u> :

Seuls les produits sélectionnés sont supprimés.

<u>Résultats réels</u> :

Certains autres produits sont également supprimés.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier ou cliquez sur le lien suivant :

[Téléchargez MDVA-10600\_EE\_2.2.3\_v1.compositeur.patch.](assets/MDVA-10600_EE_2.2.3_v1.composer.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.2.3

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce on-premise 2.1.8-2.1.14, 2.2.0-2.2.2 et 2.2.4-2.2.5
* Adobe Commerce sur l’infrastructure cloud 2.2.4-2.2.5

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.
