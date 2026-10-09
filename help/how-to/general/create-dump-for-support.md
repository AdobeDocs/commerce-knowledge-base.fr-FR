---
title: Comment créer un vidage nettoyé lorsque l’agent de support le demande
description: Cet article fournit des informations sur la création d’un vidage (sauvegarde) nettoyé de votre base de données et du code de l’administrateur Adobe Commerce lorsqu’un agent d’assistance Adobe Commerce le demande. Cette image mémoire exclut vos fichiers multimédias afin d’accélérer le processus et d’obtenir un fichier beaucoup plus petit. Toutes les données sensibles sont hachées lors de la sauvegarde de la base de données.
exl-id: ad088bd2-3f92-416e-89f0-d037d53cd6a9
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%
---
# Comment créer un vidage nettoyé lorsque l’agent de support le demande


## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) 2.3.x, 2.4.x.

## Créer une image mémoire « nettoyée »

Créez un vidage « nettoyé » à partir de l’administrateur :

1. Dans l’Administration Commerce, accédez à **Système** > **Assistance** > **Collecteur de données**.
1. Cliquez sur **Nouvelle sauvegarde**.
1. Au bout de quelques minutes, cliquez sur **État de l’actualisation** (peut prendre plus de temps, répétez l’opération toutes les 5 minutes jusqu’à ce qu’elle soit terminée).
1. Déplacez les fichiers de vidage générés du répertoire `/var/support` vers le répertoire racine Adobe Commerce.

Vous pouvez ensuite fournir à l’assistance technique le lien de téléchargement direct vers les fichiers de vidage (l’adresse de votre magasin et le nom du fichier, tels qu’ils s’affichent).

Si vous rencontrez des problèmes lors de la création des vidages à partir de l’administration, pensez à utiliser les commandes de l’interface de ligne de commande comme décrit dans la section [Exécuter les utilitaires de support](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/run-support-utilities) de notre documentation destinée aux développeurs.

## Lecture connexe

* [Créez une sauvegarde complète de la base de données pour Adobe Commerce sur l’infrastructure cloud](/help/how-to/general/create-database-dump-on-cloud.md) dans notre base de connaissances d’assistance.
