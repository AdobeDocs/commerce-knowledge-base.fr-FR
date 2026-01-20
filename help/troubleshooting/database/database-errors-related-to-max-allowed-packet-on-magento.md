---
title: Erreurs de base de données liées à max_allowed_paquets sur Adobe Commerce
description: Cet article fournit une solution pour les erreurs de connexion à la base de données dans « var/log/exception.log » qui peuvent se produire lors de l’importation d’un grand nombre de produits ou de l’exécution d’une autre tâche qui force le serveur à gérer des paquets plus volumineux que celui défini dans « max_allowed_paquet », qui est plus grand que la valeur par défaut, 16 Mo.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 5ca7a4400e62db2419b32a31a4f6cf04f5a82e35
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Erreurs de base de données liées à max_allowed_paquets sur Adobe Commerce

Cet article fournit une solution pour les erreurs de connexion à la base de données dans le `var/log/exception.log` qui peuvent se produire lors de l&#39;importation d&#39;un grand nombre de produits ou de l&#39;exécution d&#39;une autre tâche qui force le serveur à gérer des paquets plus gros que défini dans `max_allowed_packet` qui est plus grand que la valeur par défaut, 16 Mo.

## Produits et versions concernés

* Adobe Commerce On-premise, toutes les [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Lorsqu’un client [!DNL MySQL] ou le serveur [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) reçoit un paquet de plus de [max\_allowed\_paquets](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) octets, il émet une erreur [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) (visible dans le `exception.log`) et ferme la connexion. Avec certains clients, vous pouvez également obtenir une erreur *Connexion perdue à [!DNL MySQL] serveur pendant la requête* si le paquet de communication est trop volumineux.

<u>Procédure à suivre</u>

Diverses tâches peuvent générer ce problème. Cela peut inclure une tentative d’importation d’un grand nombre de produits dans Adobe Commerce ou des requêtes transactionnelles renvoyant trop de données. Il en résulte des erreurs de connexion à la base de données dans `var/log/exception.log` et d&#39;autres problèmes, comme des produits dont l&#39;importation échoue.

## Cause

La valeur par défaut de 16 Mo pour le paramètre [!DNL MySQL] `max_allowed_packets` n’est pas suffisamment élevée pour répondre à vos besoins.

## Solution

1. Identifier les requêtes dans lesquelles les lignes individuelles dépassent la limite de `max_allowed_packet` actuelle. Ces requêtes doivent être réécrites pour réduire la quantité de données renvoyées. Pour ce faire, il suffit de réduire le nombre de colonnes dans l’instruction `SELECT` ou de choisir un type de données plus petit pour différentes colonnes dans le cadre de la conception du tableau. Si vous disposez d’un compte New Relic, utilisez la page [Erreurs APM New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) la page [Bases de données APM New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) et les [Journaux New Relic](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) pour rechercher les requêtes appropriées.
1. Pour une résolution rapide, vous pouvez demander temporairement une augmentation de la taille du `max_allowed_packet` lorsque vous [soumettez un ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), mais cela est à la discrétion de l’équipe d’ingénierie client, car une valeur trop grande peut entraîner des échecs de réplication en provoquant une congestion du réseau.
1. En règle générale, il est recommandé d’exécuter la commande suivante dans l’interface de ligne de commande pour certaines de vos tables de base de données volumineuses :

   ```
   show table status like [table name to match]
   ```

   Évaluez les requêtes exécutées sur ces tables pour déterminer si vous dépassez la taille de `max_allowed_packet` recommandée de 16 Mo. Suivez le même processus à l’étape 1 pour réduire les données renvoyées par de telles requêtes.

## Lecture connexe

* [Présentation de l’installation sur site](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/overview) dans notre documentation destinée aux développeurs.
* [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=fr) dans notre base de connaissances d’assistance.
* [Bonnes pratiques pour résoudre les problèmes de performances de la base de données](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=fr) dans notre base de connaissances d’assistance.
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
