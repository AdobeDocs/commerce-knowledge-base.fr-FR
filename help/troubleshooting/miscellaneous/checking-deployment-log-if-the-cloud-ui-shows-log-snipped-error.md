---
title: Vérification du journal de déploiement si l’interface utilisateur de Cloud a "extrait de journal"
description: Cet article fournit une solution au problème où l’interface utilisateur d’Adobe Commerce sur l’infrastructure cloud affiche le *fragment de journal car il s’agissait d’un message d’erreur trop long* lors de la tentative d’affichage du journal de déploiement sur l’interface utilisateur du projet cloud.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
source-git-commit: 71bec5b99063d771982f6dcab111b9e5a4aaec69
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Vérification du journal de déploiement si l’interface utilisateur de cloud comporte *fragment de journal* error

Cet article fournit une solution au problème où l’interface utilisateur d’Adobe Commerce sur l’infrastructure cloud affiche la variable *fragment de journal car il était trop long* message d’erreur lors de la tentative d’affichage du journal de déploiement sur l’interface utilisateur du projet cloud. (Ne s’applique pas à la variable [Console Adobe Commerce Cloud](https://console.adobecommerce.com/).)

## Produits concernés

Adobe Commerce sur l’infrastructure cloud (toutes les versions prises en charge)

## Problème

Lors de la tentative d’affichage du journal de déploiement sur l’interface utilisateur du projet cloud, Adobe Commerce sur l’interface utilisateur de l’infrastructure cloud affiche le message d’erreur suivant : *fragment de journal car il était trop long*.

## Étapes à reproduire

1. Accédez à l’URL du projet et cliquez sur le **État** du déploiement en question.
1. Si le journal est trop long pour s’afficher dans l’interface utilisateur, le message d’erreur s’affiche : *fragment de journal car il était trop long*.

## Cause

Notez que le journal affiché dans l’interface utilisateur ne doit pas être traité comme la source de vérité, en particulier si vous constatez que le site ne répond pas ou ne fonctionne pas correctement une fois le déploiement répertorié avec l’état Réussite. Vous devez également vérifier avec les journaux sur le serveur. Voir [Affichage et gestion des journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) dans notre documentation destinée aux développeurs.

## Solution

1. Assurez-vous que vous avez [Interface de ligne de commande de Magento Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html) installé dans votre environnement local.
1. Exécutez la commande suivante :

   ```bash
   magento-cloud activity -p <project id> -e <environment>
   ```

1. Elle renvoie une sortie similaire à celle-ci :

   ```bash
   Activities on the project <project name> (project id), environment <environment>:
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | ID            | Created                   | Description                         | Progress | State    | Result  |
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | l5wgwmzwrsskg | 2021-06-01T08:18:02-07:00 | ABC merged Integration into Staging | 100%     | complete | success |
   | raah5xrhqz3wg | 2021-06-01T08:07:18-07:00 | XYZ pushed to Integration           | 100%     | complete | failure |
   ```

1. Copiez l’ID d’activité du déploiement concerné, puis exécutez la commande :

   ```bash
   magento-cloud activity:log <activity ID> -p <project id> -e <environment>
   ```

   Exemple pour examiner le journal du déploiement en échec :

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## Lectures connexes dans notre documentation destinée aux développeurs :

* [Adobe Commerce sur l’infrastructure cloud > Créer et déployer](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)
* [Adobe Commerce sur l’infrastructure cloud > Afficher et gérer les journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
