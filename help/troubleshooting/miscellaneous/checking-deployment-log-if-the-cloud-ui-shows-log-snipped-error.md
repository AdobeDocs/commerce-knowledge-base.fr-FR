---
title: Vérification du journal de déploiement si l’interface utilisateur de Cloud comporte une erreur « journal arrêté »
description: Cet article fournit une solution au problème où l’interface utilisateur d’Adobe Commerce sur l’infrastructure cloud affiche le message d’erreur *journal arrêté car il était trop long* lors de la tentative d’affichage du journal de déploiement sur l’interface utilisateur du projet cloud.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%
---
# Vérification du journal de déploiement en cas d’erreur *journal coupé* dans l’interface utilisateur du cloud

Cet article fournit une solution au problème d’affichage du message d’erreur *journal extrait car trop long* dans l’interface utilisateur d’Adobe Commerce sur l’infrastructure cloud lors de la tentative d’affichage du journal de déploiement dans l’interface utilisateur du projet cloud. (Ne s’applique pas à la [console Adobe Commerce Cloud](https://console.adobecommerce.com/).)

## Produits concernés

Adobe Commerce sur les infrastructures cloud (toutes les versions prises en charge)

## Problème

Lors de la tentative d’affichage du journal de déploiement dans l’interface utilisateur du projet cloud, l’interface utilisateur d’Adobe Commerce sur l’infrastructure cloud affiche le message d’erreur suivant : *journal ignoré, car il était trop long*.

## Procédure à suivre

1. Accédez à l’URL du projet et cliquez sur le **Statut** du déploiement en question.
1. Si le journal est trop long pour être affiché dans l’interface utilisateur, le message d’erreur suivant s’affiche : *journal coupé car il était trop long*.

## Cause

Notez que le journal affiché dans l’interface utilisateur ne doit pas être traité comme la source de vérité, en particulier si vous constatez que le site ne répond pas ou ne fonctionne pas correctement après que le déploiement a été répertorié avec le statut Succès . Vous devez également vérifier avec les journaux sur le serveur. Voir [Afficher et gérer les journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=fr) dans notre documentation destinée aux développeurs.

## Solution

1. Assurez-vous que l’interface de ligne de commande [Magento Cloud CLI](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html?lang=fr) est installée dans votre environnement local.
1. Vous pouvez exécuter l’une des commandes suivantes :

   ```bash
   magento-cloud act -p <project id> -e <environment>
   ```

   ```bash
   magento-cloud activity:list -p <project id> -e <environment>
   ```

1. Ils renvoient une sortie similaire à celle-ci :

   ```bash
   Activities on the project <project name> (project id), environment <environment>:
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | ID            | Created                   | Description                         | Progress | State    | Result  |
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | l5wgwmzwrsskg | 2021-06-01T08:18:02-07:00 | ABC merged Integration into Staging | 100%     | complete | success |
   | raah5xrhqz3wg | 2021-06-01T08:07:18-07:00 | XYZ pushed to Integration           | 100%     | complete | failure |
   ```

1. Copiez l’ID d’activité du déploiement affecté, puis exécutez la commande :

   ```bash
   magento-cloud activity:log <activity ID> -p <project id> -e <environment>
   ```

   Exemple pour examiner le journal du déploiement ayant échoué :

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## Informations connexes dans notre documentation destinée aux développeurs :

* [Adobe Commerce sur l’infrastructure cloud > Créer et déployer](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=fr)
* [Adobe Commerce sur les infrastructures cloud > Afficher et gérer les journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=fr)
