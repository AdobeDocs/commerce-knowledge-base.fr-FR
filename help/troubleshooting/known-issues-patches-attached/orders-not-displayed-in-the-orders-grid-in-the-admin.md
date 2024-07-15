---
title: Commandes non affichées dans la grille Commandes de l’Admin
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.1 lié aux commandes qui ne s’affichent pas dans la grille Commandes de l’administrateur Commerce.
exl-id: b8376760-6558-41ed-8c6b-51c5759e831a
feature: Admin Workspace, B2B, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Commandes non affichées dans la grille Commandes de l’Admin

Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.1 lié aux commandes qui ne s’affichent pas dans la grille Commandes de l’administrateur Commerce.

## Problème

Dans Adobe Commerce 2.2.1 avec l’extension B2B installée, les commandes créées sur le storefront par un client enregistré ne s’affichent pas dans la liste des commandes du compte du client dans l’administrateur Commerce. Dans le journal de débogage (`./var/log/debug.log`), l’erreur suivante est consignée :

`report.CRITICAL: You cannot define a correlation name ‘company_order’ more than once`

<u>Conditions préalables</u> :

Votre catalogue de magasins contient des produits, et non des exemples de données Adobe Commerce, et l’extension B2B est installée.

<u>Étapes à reproduire</u> :

1. Accédez à l’interface du magasin et créez un compte client.
1. Ajoutez un produit au panier, effectuez le passage en caisse et envoyez une commande.
1. Connectez-vous à l’administrateur.
1. Accédez à **Customers,** puis sélectionnez **All Customers**.
1. Pour le client nouvellement créé, cliquez sur **Modifier**.
1. Cliquez sur **Commandes** dans le panneau de gauche.

<u>Résultat attendu</u> :

La commande récemment envoyée est répertoriée dans la grille.

<u>Résultat réel</u> :

La grille Commandes ne s’affiche pas. Une page vierge s’affiche à la place.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[Téléchargez MDVA-7868\_EE\_2.2.1\_v1\_compositeur.patch.](assets/MDVA-7868_EE_2.2.1_v1_composer.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce on-premise 2.2.1

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud de la version 2.2.0 à 2.2.3
* Adobe Commerce on-premise 2.2.0 et 2.2.2 à 2.2.3

## Comment appliquer le correctif

Pour obtenir des instructions, reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.

## Fichiers attachés
