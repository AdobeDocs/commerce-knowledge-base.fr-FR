---
title: Deadlocks dans MySQL
description: Cet article traite des blocages de MySQL pour aider à les identifier et à les résoudre s’ils provoquent la panne d’un site, l’importation de base de données bloquée ou d’autres problèmes Adobe Commerce.
exl-id: 529d1c0b-77f3-4604-9878-e7ea2c9c3640
feature: Best Practices, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Deadlocks dans MySQL

Cet article traite des blocages de MySQL pour aider à les identifier et à les résoudre s’ils provoquent la panne d’un site, l’importation de base de données bloquée ou d’autres problèmes Adobe Commerce.

## Produits et versions concernés

* Adobe Commerce sur site 2.2.x et 2.3.x
* Adobe Commerce sur l’infrastructure cloud 2.2.x et 2.3.x

## Problème

Dans MySQL, des blocages sont bloqués et des demandes de verrouillage se produisent lorsque plusieurs transactions sont bloquées. Les horloges présentes n’indiquent pas toujours un problème, mais sont souvent le symptôme d’un autre problème MySQL ou Adobe Commerce qui s’est produit.

Souvent, les journaux d’application, de déploiement ou MySQL mentionnent une erreur *&quot;blocage&quot;* ou l’erreur *&quot;blocage détecté lors de la tentative de verrouillage ; essayez de redémarrer la transaction.&quot;*

## Cause

Les blocages de compte peuvent avoir plusieurs causes, mais le plus courant est si vous effectuez une interaction (web/processes/cron jobs/autres utilisateurs/maintenance MySQL/imports MySQL) tout en exécutant des requêtes DML/DDL en même temps.

Par exemple, il est recommandé d’éviter un import de base de données MySQL bloqué en mettant d’abord votre site en mode de maintenance afin d’éviter d’envoyer des requêtes SQL vers la base de données, ce qui pourrait entraîner des blocages et un import de base de données bloqué.

## Solution

1. Recherchez les erreurs de blocage dans les journaux d’application, de déploiement ou MySQL :
   * [Emplacements des journaux Adobe Commerce et Magento Open Source](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/enable-logging.html)
   * [Adobe Commerce sur les emplacements des journaux d’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
1. Vérifiez votre liste de processus MySQL pour exécuter des processus avec la commande `mysql -e 'show full processlist';`.
1. Si vous utilisez Adobe Commerce sur l’infrastructure cloud, vérifiez que l’esclave MySQL est activé. Consultez cet article : [Déployer des variables (MYSQL\_USE\_SLAVE\_CONNECTION)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection).
1. Selon les erreurs impliquées, la solution peut se présenter ou vous devrez peut-être inclure vos informations de journal si vous devez ouvrir un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lecture connexe

* [Comment réduire et gérer les blocages de date](https://dev.mysql.com/doc/refman/5.7/en/innodb-deadlocks-handling.html)
* [Optimisation de l’indexeur - Changement de tableau de l’indexeur](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
* [Opérations en bloc - Consommer des messages](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

>[!NOTE]
>
>Nous sommes conscients que cet article peut encore contenir des termes logiciels standard que certains peuvent trouver racistes, sexistes ou oppressifs et qui peuvent faire que le lecteur se sent blessé, traumatisé ou mal accueilli. Adobe s’efforce de supprimer ces termes de notre code, de notre documentation et de nos expériences utilisateur.
