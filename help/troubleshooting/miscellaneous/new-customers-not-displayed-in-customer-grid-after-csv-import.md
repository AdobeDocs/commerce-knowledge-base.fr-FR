---
title: Nouveaux clients non affichés dans la grille des clients après l’importation CSV
description: Cet article fournit un correctif pour le problème lorsque vous ne pouvez pas voir de nouveaux clients sous **Customers** &gt; **Tous les clients** après une importation à partir d’un fichier `.csv`. La solution consiste à définir l’indexeur `customer_grid` sur le mode "Mise à jour lors de l’enregistrement" et à réindexer manuellement la grille du client.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Nouveaux clients non affichés dans la grille des clients après l’importation CSV

Cet article fournit un correctif pour le problème lorsque vous ne pouvez pas voir de nouveaux clients sous **Clients** > **Tous les clients** après un import depuis un `.csv` fichier . La solution consiste à définir la variable `customer_grid` indexeur en mode &quot;Mise à jour sur enregistrement&quot; et réindexez manuellement la grille du client.

## Versions affectées

* Adobe Commerce on-premise 2.2.0 et versions ultérieures
* Adobe Commerce sur l’infrastructure cloud 2.2.0 et versions ultérieures

## Problème

Après avoir importé de nouveaux clients à partir d’un `.csv` à l’aide de la fonctionnalité d’importation Adobe Commerce native, vous ne pourrez peut-être pas voir les nouveaux enregistrements de client sous **Clients** > **Tous les clients** dans l’Admin jusqu’à ce que vous réindexiez manuellement la variable `customer_grid` indexeur.

## Cause

Le mode d’indexation &quot;Mise à jour lors de la planification&quot; dans Adobe Commerce 2.2.0 et versions ultérieures ne prend pas en charge `customer_grid` indexeur en raison de problèmes de performances.

## Solution

Configurez la variable `customer_grid` indexeur à réindexer à l’aide du mode &quot;Mettre à jour sur l’enregistrement&quot;. Pour ce faire, procédez comme suit :

1. Connectez-vous à l’administrateur Commerce.
1. Cliquez sur **Système** > **Outils** > **Gestion des index**.
1. Cochez la case en regard de l’indexeur de grille client.
1. Dans le **Actions** liste déroulante, sélectionnez *Mettre à jour lors de l’enregistrement*.
1. Cliquez sur **Envoyer**.

Nous vous recommandons également de réindexer manuellement la variable `customer_grid` indexeur après avoir configuré le mode d’indexation pour s’assurer que l’index est à jour et peut fonctionner avec cron. Pour réindexer manuellement, utilisez la commande suivante :

`bin/magento indexer:reindex customer_grid`

## Informations supplémentaires

Liens vers des sujets connexes dans notre documentation destinée aux développeurs :

* [Présentation de l’indexation](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [Gestion des indexeurs](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
