---
title: Consultez les problèmes de Secondaires sur Adobe Commerce Cloud 2.4.6 avec MariaDB 10.6
description: Cet article explique comment résoudre les problèmes de lecture de Secondaires sur Adobe Commerce Cloud 2.4.6 avec MariaDB 10.6.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: 724a30310c3841f8280628436925f9a3e5933b14
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Consultez les problèmes de Secondaires sur Adobe Commerce Cloud 2.4.6 avec MariaDB 10.6

Cet article fournit des solutions pour les comportements inattendus lors de l’utilisation de la lecture de Secondaires sur Adobe Commerce Cloud 2.4.6 avec MariaDB 10.6+.

## Produits et versions concernés

* MariaDB 10.6+
* Adobe Commerce sur les infrastructures cloud 2.4.6

## Problème

Les lectures non critiques affichent des informations incorrectes.

## Cause

La configuration `slave_parallel_mode` de la base de données a été modifiée par défaut en *optimistics* lorsque la valeur doit être *conservatrice* et que la valeur `synchronous_replication` dans Ece-Tools est définie par défaut sur *true* lorsque la valeur doit être *false*.

## Solution

1. Vérifiez que le paramètre `slave_parallel_mode` est défini sur *conservateur* (vous devrez [créer un ticket d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=fr#submit-ticket) si la valeur ne s’affiche pas comme *conservateur*). Pour vérifier, exécutez la commande suivante :

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. Mettez à jour les configurations de la base de données `.magento.env.yaml` vers :

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



Pour connaître la procédure de mise à jour de la configuration de la base de données, reportez-vous à la section [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=fr#database_configuration) de la rubrique Déploiement des variables du guide Commerce sur les infrastructures cloud.


## Lecture connexe

* [Configurez les variables d’environnement pour le déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=fr) dans le guide Commerce sur les infrastructures cloud.
* [Bonnes pratiques relatives à la configuration de la base de données](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=fr) dans le guide d’implémentation.
