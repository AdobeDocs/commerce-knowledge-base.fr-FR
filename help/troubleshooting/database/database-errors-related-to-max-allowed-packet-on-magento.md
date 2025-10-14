---
title: Erreurs de base de données liées à max_allowed_packet sur Adobe Commerce
description: Cet article fournit une solution pour les erreurs de connexion à la base de données dans "var/log/exception.log" qui peuvent se produire lors de l’importation d’un grand nombre de produits ou de l’exécution d’une autre tâche qui force le serveur à gérer des paquets plus volumineux que celui défini dans "max_allowed_packet" qui est plus grand que la valeur par défaut, 16 Mo.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Erreurs de base de données liées à max_allowed_packet sur Adobe Commerce

Cet article fournit une solution pour les erreurs de connexion à la base de données dans le `var/log/exception.log` qui peuvent se produire lors de l’importation d’un grand nombre de produits ou de l’exécution d’une autre tâche qui force le serveur à gérer des paquets plus volumineux que celui défini dans `max_allowed_packet` qui est supérieur à la taille par défaut de 16 Mo.

## Produits et versions concernés

* Adobe Commerce sur site, toutes les [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Lorsqu&#39;un client [!DNL MySQL] ou le serveur [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) reçoit un paquet supérieur à [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet)&rbrace;, il génère une erreur [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) (qui peut être vue dans `exception.log`) et ferme la connexion. Avec certains clients, vous pouvez également obtenir une *connexion perdue au serveur [!DNL MySQL] lors de la requête* si le paquet de communication est trop volumineux.

<u>Étapes à reproduire</u>

Plusieurs tâches peuvent produire ce problème. Cela peut inclure la tentative d’importation d’un grand nombre de produits dans Adobe Commerce ou des requêtes transactionnelles renvoyant trop de données. Il en résulte des erreurs de connexion à la base de données dans `var/log/exception.log` et d’autres problèmes, comme des produits qui n’ont pas été importés avec succès.

## Cause

La valeur par défaut de 16 Mo pour le paramètre [!DNL MySQL] `max_allowed_packets` n’est pas assez grande pour répondre à vos besoins.

## Solution

1. Identifiez les requêtes pour lesquelles les lignes individuelles dépassent la limite actuelle de `max_allowed_packet`. De telles requêtes doivent être réécrites afin de réduire la quantité de données renvoyées. Pour ce faire, vous pouvez inclure un plus petit nombre de colonnes dans l’instruction `SELECT` ou choisir un type de données plus petit pour diverses colonnes dans la conception de tableau. Si vous disposez d’un compte New Relic, utilisez la [page Erreurs APM New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) et la [page Bases de données New Relic APM](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) et les [journaux New Relic](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) pour rechercher les requêtes appropriées.
1. Pour une correction rapide, vous pouvez temporairement demander une augmentation de la taille `max_allowed_packet` lorsque vous [&#x200B; envoyez un ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), mais c’est à la discrétion de l’équipe d’ingénierie du client, car une valeur trop importante peut entraîner des échecs de réplication en provoquant des embouteillages du réseau.
1. Pour certaines de vos tables de base de données volumineuses, il est recommandé d’exécuter la commande suivante dans l’interface de ligne de commande :

   ```
   show table status like [table name to match]
   ```

   Évaluez les requêtes exécutées sur ces tables pour déterminer si vous dépassez la taille recommandée de `max_allowed_packet` de 16 Mo. Suivez la même procédure à l’étape 1 pour réduire les données renvoyées par de telles requêtes.

## Lecture connexe

* [Présentation de l’installation sur site](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/overview) dans notre documentation destinée aux développeurs.
* [Le chargement de la base de données perd la connexion à [!DNL MySQL]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql) dans notre base de connaissances de support.
* [Bonnes pratiques de base de données pour Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=fr) dans notre base de connaissances d’assistance.
* [Bonnes pratiques pour résoudre les problèmes de performances de la base de données](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=fr) dans notre base de connaissances de support.
* [&#x200B; Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
