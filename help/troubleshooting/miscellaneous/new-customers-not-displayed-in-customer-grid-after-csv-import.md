---
title: Nouveaux clients non affichés dans la grille des clients après l’importation CSV
description: Cet article fournit un correctif pour le problème lorsque vous ne pouvez pas voir de nouveaux clients sous **Customers** &gt; **Tous les clients** après une importation à partir d’un fichier &grave;.csv&grave;. La solution consiste à définir l’indexeur &grave;customer_grid&grave; sur le mode "Mise à jour lors de l’enregistrement" et à réindexer manuellement la grille du client.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Nouveaux clients non affichés dans la grille des clients après l’importation CSV

Cet article fournit un correctif pour le problème lorsque vous ne pouvez pas voir de nouveaux clients sous **Customers** > **Tous les clients** après une importation à partir d’un fichier `.csv`. La solution consiste à définir l’indexeur `customer_grid` sur le mode &quot;Mettre à jour lors de l’enregistrement&quot; et à réindexer manuellement la grille du client.

## Versions affectées

* Adobe Commerce on-premise 2.2.0 et versions ultérieures
* Adobe Commerce sur l’infrastructure cloud 2.2.0 et versions ultérieures

## Problème

Après avoir importé de nouveaux clients à partir d’un fichier `.csv` à l’aide de la fonctionnalité d’importation native d’Adobe Commerce, il se peut que vous ne puissiez pas voir les nouveaux enregistrements de client sous **Customers** > **Tous les clients** dans l’administrateur tant que vous n’avez pas réindexé manuellement l’indexeur `customer_grid`.

## Cause

Le mode d’indexation &quot;Mise à jour lors de la planification&quot; dans Adobe Commerce 2.2.0 et versions ultérieures ne prend pas en charge l’indexeur `customer_grid` en raison de problèmes de performances.

## Solution

Configurez l&#39;indexeur `customer_grid` à réindexer à l&#39;aide du mode &quot;Mettre à jour lors de l&#39;enregistrement&quot;. Pour ce faire, procédez comme suit :

1. Connectez-vous à l’administrateur Commerce.
1. Cliquez sur **Système** > **Outils** > **Gestion des index**.
1. Cochez la case en regard de l’indexeur de grille client.
1. Dans la liste déroulante **Actions**, sélectionnez *Mettre à jour sur Enregistrer*.
1. Cliquez sur **Submit**.

Nous vous recommandons également de réindexer manuellement l’indexeur `customer_grid` après avoir configuré le mode d’indexation pour vous assurer que l’index est à jour et peut fonctionner avec cron. Pour réindexer manuellement, utilisez la commande suivante :

`bin/magento indexer:reindex customer_grid`

## Informations supplémentaires

Liens vers des sujets connexes dans notre documentation destinée aux développeurs :

* [Présentation de l’indexation](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [Gérer les indexeurs](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers)
