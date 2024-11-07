---
title: Comment créer un vidage "frotté" sur demande de l’agent d’assistance
description: Cet article fournit des informations sur la création d’un vidage (sauvegarde) "frotté" de votre base de données et de code à partir de l’administrateur Adobe Commerce lorsque celui-ci est invité à en fournir un par un agent de support Adobe Commerce. Ce vidage exclut vos fichiers multimédias afin d’accélérer le processus et de générer un fichier beaucoup plus petit. Toutes les données sensibles sont hachées lors de la sauvegarde de la base.
exl-id: ad088bd2-3f92-416e-89f0-d037d53cd6a9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Comment créer un vidage &quot;frotté&quot; sur demande de l’agent d’assistance


## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) 2.3.x, 2.4.x.

## Créer un vidage &quot;frotté&quot;

Créez un vidage &quot;frotté&quot; à partir de l’administrateur :

1. Dans l’administrateur Commerce, accédez à **Système** > **Assistance** > **Collecteur de données**.
1. Cliquez sur **Nouvelle sauvegarde**.
1. Après quelques minutes, cliquez sur **Actualiser l’état** (ce qui peut prendre plus de temps, répétez toutes les 5 minutes jusqu’à ce qu’il soit terminé).
1. Délocalisez les fichiers de vidage générés du répertoire `/var/support` vers le répertoire racine Adobe Commerce.

Vous pouvez ensuite fournir pour prendre en charge le lien de téléchargement direct vers les fichiers de vidage (l’adresse de votre magasin et le nom du fichier tel qu’affiché).

Si vous rencontrez des problèmes lors de la création de vidages à partir de l’administrateur, pensez à utiliser les commandes de l’interface de ligne de commande comme décrit dans la section [Exécution des utilitaires de support](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/run-support-utilities) de notre documentation destinée aux développeurs.

## Lecture connexe

* [ Créez une sauvegarde complète de la base de données pour Adobe Commerce sur l’infrastructure cloud ](/help/how-to/general/create-database-dump-on-cloud.md) dans notre base de connaissances de support.
