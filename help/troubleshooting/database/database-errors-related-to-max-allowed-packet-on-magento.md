---
title: Erreurs de base de données liées à max_allowed_packet sur Adobe Commerce
description: Cet article fournit une solution pour les erreurs de connexion à la base de données dans "var/log/exception.log" qui peuvent se produire lors de l’importation d’un grand nombre de produits ou de l’exécution d’une autre tâche qui force le serveur à gérer des paquets plus volumineux que celui défini dans "max_allowed_packet" qui est plus grand que la valeur par défaut, 16 Mo.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Erreurs de base de données liées à max_allowed_packet sur Adobe Commerce

Cet article fournit une solution aux erreurs de connexion à la base de données dans la variable `var/log/exception.log` qui peuvent survenir lors de l’importation d’un grand nombre de produits ou lors d’une autre tâche qui force le serveur à gérer des paquets plus volumineux que ceux définis dans `max_allowed_packet` supérieur à la valeur par défaut, 16 Mo.

## Produits et versions concernés

* Adobe Commerce sur site, toutes [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Lorsqu’un client MySQL ou la variable [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) le serveur reçoit un paquet plus grand que [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) octets, il émet une [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) (qui s’affiche dans la variable `exception.log`) et ferme la connexion. Avec certains clients, vous pouvez également obtenir une *Perte de la connexion au serveur MySQL lors de la requête* s’il s’agit d’un paquet de communication trop grand.

<u>Étapes à reproduire</u>

Plusieurs tâches peuvent produire ce problème. Cela peut inclure la tentative d’importation d’un grand nombre de produits dans Adobe Commerce ou des requêtes transactionnelles renvoyant trop de données. Le résultat est une erreur de connexion à la base de données dans `var/log/exception.log` et d’autres problèmes, comme le fait que les produits n’aient pas été importés avec succès.

## Cause

La valeur par défaut de 16 Mo pour MySQL. `max_allowed_packets` n’est pas assez grande pour répondre à vos besoins.

## Solution

1. Identifier les requêtes lorsque les lignes individuelles dépassent la ligne actuelle `max_allowed_packet` limite. De telles requêtes doivent être réécrites afin de réduire la quantité de données renvoyées. Pour ce faire, il suffit d’avoir un plus petit nombre de colonnes dans la variable `SELECT` ou en choisissant un type de données plus petit pour différentes colonnes dans le cadre de la conception de tableau. Si vous disposez d’un compte New Relic, utilisez la variable [Page des erreurs New Relic APM](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) et la variable [Page Bases de données New Relic APM](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time), et [Journaux New Relic](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) pour rechercher les requêtes pertinentes.
1. Pour une correction rapide, vous pouvez temporairement demander la `max_allowed_packet` taille à augmenter lorsque vous [envoi d’un ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), mais c’est à la discrétion de l’équipe d’ingénierie du client, car une valeur trop élevée peut entraîner des échecs de réplication en provoquant des embouteillages du réseau.
1. Pour certaines de vos tables de base de données volumineuses, il est recommandé d’exécuter la commande suivante dans l’interface de ligne de commande :

   ```
   show table status like [table name to match]
   ```

   Evaluez les requêtes exécutées sur ces tables pour déterminer si vous dépassez les valeurs recommandées. `max_allowed_packet` taille de 16 Mo. Suivez la même procédure à l’étape 1 pour réduire les données renvoyées par de telles requêtes.

## Lecture connexe

* [Guide d’installation > MySQL](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) dans notre documentation destinée aux développeurs.
* [Le chargement de la base de données perd la connexion à MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) dans notre base de connaissances de soutien.
* [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) dans notre base de connaissances de soutien.
* [Bonnes pratiques pour résoudre les problèmes de performances de la base de données](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) dans notre base de connaissances de soutien.
