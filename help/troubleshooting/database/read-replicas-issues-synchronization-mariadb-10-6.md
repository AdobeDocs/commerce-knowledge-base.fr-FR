---
title: Lecture des problèmes de Secondaire sur Adobe Commerce Cloud 2.4.6 avec MariaDB 10.6
description: Cet article explique comment résoudre les problèmes de lecture de Secondaires sur Adobe Commerce Cloud 2.4.6 avec MariaDB 10.6.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Lecture des problèmes de Secondaire sur Adobe Commerce Cloud 2.4.6 avec MariaDB 10.6

Cet article fournit des solutions pour les comportements inattendus lors de l’utilisation de la lecture de Secondaires sur Adobe Commerce Cloud 2.4.6 avec MariaDB 10.6+.

## Produits et versions concernés

* MariaDB 10.6+
* Adobe Commerce sur l’infrastructure cloud 2.4.6

## Problème

Les lectures non critiques affichent des informations incorrectes.

## Cause

La variable `slave_parallel_mode` La configuration de la base de données a été remplacée par défaut par *optimistics* lorsque la valeur doit être *conservateur*, et la variable `synchronous_replication` dans Ece-Tools est définie par défaut sur *true* lorsque la valeur doit être *false*.

## Solution

1. Vérifiez que la variable `slave_parallel_mode` est défini sur *conservateur* (vous devrez [lever un ticket d’assistance](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) si la valeur n’est pas affichée comme *conservateur*). Pour vérifier, exécutez la commande suivante :

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. Mettre à jour `.magento.env.yaml` les configurations de base de données pour :

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



Pour les étapes de mise à jour de la configuration de la base de données, reportez-vous à la section [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration) dans la rubrique Déploiement de variables du guide Commerce on Cloud Infrastructure.


## Lecture connexe

* [Configuration des variables d’environnement pour le déploiement](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) dans le guide Commerce on Cloud Infrastructure.
* [Bonnes pratiques relatives à la configuration des bases de données](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) dans le manuel relatif à l’implémentation.
