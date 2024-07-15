---
title: Résolution des problèmes liés aux rapports avancés pour Adobe Commerce
description: Les problèmes de création de rapports avancés sur Adobe Commerce peuvent être résolus à l’aide de cet outil de dépannage. Cela inclut le reporting avancé qui n’affiche aucune donnée et aucune erreur 404. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’outil de dépannage.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 84b4ca4c4144381f0b404d2eae6684e7b21755df
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Résolution des problèmes liés aux rapports avancés pour Adobe Commerce

Les problèmes de création de rapports avancés sur Adobe Commerce peuvent être résolus à l’aide de cet outil de dépannage. Cela inclut le reporting avancé qui n’affiche aucune donnée et aucune erreur 404. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’outil de dépannage.

## Étape 1 - Confirmation que le site respecte les exigences de création de rapports avancées {#step-1}

+++**Votre site web répond-il à des exigences de création de rapports avancées ?**

Vous disposez d’une page Erreur 404 lors de l’utilisation du reporting avancé. Votre site web est-il conforme aux [exigences de création de rapports avancées](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements) ?

a. OUI - Passez à l’ [étape 2](#step-2).\
b. NON - Renseignez les exigences de création de rapports avancées pour votre site en suivant les étapes de la section [Exigences de création de rapports avancées](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements). Ensuite, passez à l’ [étape 2](#step-2).

+++

## Etape 2 - Y a-t-il des commandes dans plusieurs devises de base ? {#step-2}

+++**Plusieurs devises de base sont-elles utilisées ?**

Plusieurs devises de base sont-elles utilisées (dans les commandes et la configuration) ? Exécutez cette commande SQL pour obtenir la configuration actuelle : `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. OUI - Si plusieurs lignes sont renvoyées par la requête, vous ne pouvez pas utiliser la création de rapports avancés, car nous ne prenons en charge qu’une seule devise.\
b. NON - La sortie n’affiche qu’une seule devise. Exemple : `USD`. Plusieurs devises de base ont-elles déjà été utilisées (dans les commandes) ? Exécutez cette commande SQL pour obtenir les données des commandes historiques :\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**REMARQUE : cette commande nécessite une analyse de table complète. Pour les tables avec un grand nombre d&#39;enregistrements, cela peut avoir un impact sur les performances pendant l&#39;exécution de la requête** pour obtenir des données de commandes historiques.
Si plusieurs devises de base ont jamais été utilisées, vous ne pouvez pas utiliser la création de rapports avancés, car nous ne prenons en charge qu’une seule devise. Si la sortie n’affiche qu’une seule devise, passez à l’ [étape 3](#step-3).

+++

## Etape 3 - Vérifier si la base de données partagée est utilisée {#step-3}

+++**Utilisez-vous la solution de base de données partagée ?**

Utilisez-vous la [solution de base de données partagée](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html) ?

a. OUI - Utilisez le correctif **MDVA-26831** dans [l’erreur Advanced Reporting 404 sur la solution de base de données partagée](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-404-error-on-split-database-solution.md) et effacez le cache. Patientez 24 heures pendant que la tâche s’exécute à nouveau et réessayez.\
b. NO - Passez à [Étape 4](#step-4).

+++

## Étape 4 - Confirmation de l’activation des rapports avancés {#step-4}

+++**La création de rapports avancés est-elle activée ?**

Cochez **Admin** > **Magasins** > **Paramètres** > **Configuration** > **Général** > **Avancé**. Pour obtenir des instructions détaillées, consultez la section [Création de rapports avancés : activer la création de rapports avancés](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting).

a. OUI - Passez à l’ [étape 5](#step-5).\
b. NO - [Activez les rapports avancés](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) et enregistrez-les, puis attendez 24 heures que les rapports avancés et Adobe Commerce se synchronisent. Vérifiez si vos données sont désormais chargées. Si c&#39;est le cas, vous avez résolu le problème. S’il ne passe pas à [Étape 5](#step-5).

+++

## Étape 5 - Rechercher un jeton {#step-5}

+++**Y a-t-il un jeton ?**

Vérifiez qu’il existe un jeton en exécutant la requête suivante : `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` Existe-t-il un jeton ?

a. OUI - Passez à l’ [étape 7](#step-7).\
b. NO - Si la valeur du jeton est NULL ou s’il n’y a aucun enregistrement dans la base de données, passez à l’ [Étape 6](#step-6).

+++

## Étape 6 - Utilisation de la ligne {#step-6}

+++**La requête renvoie-t-elle la ligne ?**

Vérifiez la valeur du compteur dans la table des indicateurs en exécutant cette requête : ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` La requête renvoie-t-elle la ligne ?

a. OUI - Effectuez les étapes suivantes : 1. Exécutez la requête ci-dessous :\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [Désactivez et activez le module de création de rapports avancé](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) dans les paramètres et [réautorisez le jeton](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
3\. Patientez 24 heures pour la synchronisation d’Adobe Commerce et des rapports avancés. Si vous ne pouvez toujours pas voir les données dans les rapports avancés, [soumettez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Si la requête ne renvoie rien, procédez comme suit : 1. [Désactivez et activez le module de création de rapports avancé](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) dans les paramètres et [réautorisez le jeton](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
2\. Patientez 24 heures pour la synchronisation d’Adobe Commerce et des rapports avancés. Si vous ne pouvez toujours pas voir les données dans les rapports avancés, [soumettez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Étape 7 - Recherche d&#39;enregistrements dans la table `cron_schedule` {#step-7}

+++**Existe-t-il des enregistrements dans la table `cron_schedule` ?**

Vérifiez que la tâche `analytics_collect_data` a été exécutée en exécutant cette requête : `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. OUI - S’il existe des enregistrements et que la colonne **status** indique _manqué_, utilisez le correctif dans cet article de la base de connaissances [Mettre à jour les rapports avancés pour fonctionner sur son propre groupe cron](/help/troubleshooting/known-issues-patches-attached/update-advanced-reporting-to-run-on-its-own-cron-group.md).\
b. OUI - S’il existe des enregistrements et que la colonne **status** indique _success_, passez à l’ [étape 9](#step-9).\
c. OUI - S’il existe des enregistrements et que la colonne **status** indique _error_, passez à l’ [étape 8.](#step-8)\
d. NO - S’il n’existe aucun enregistrement, passez à l’ [étape 8](#step-8).

+++

## Étape 8 - Rechercher une tâche dans `support_report.log` {#step-8}

+++**La tâche a-t-elle été connectée à `support_report.log` ?**

Exécutez la commande : `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. OUI - Si la sortie de la requête indique une tâche réussie, par exemple `Cron Job analytics_collect_data is successfully finished` passez à l’ [étape 9](#step-9).\
b. NON - S’il n’y a aucun enregistrement dans le journal, [soumettez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. OUI - S’il existe des enregistrements mais qu’une erreur s’est produite, passez à l’[étape 10](#step-10).

+++

## Étape 9 - Recherchez le fichier `data.tgz` {#step-9}

+++**Le fichier `data.tgz` existe-t-il dans le système et des enregistrements sont-ils présents dans les journaux d’accès ?**

Pour vérifier que le fichier `data.tgz` existe, exécutez la commande :

```
ls -ltr pub/media/analytics/<there should be a directory with hash name>/
```

Pour vérifier qu’il existe des enregistrements dans access.logs, exécutez la commande :

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

a. OUI - Si le fichier `data.tgz` est présent et que des enregistrements sont présents dans les journaux d’accès, mais que vous avez toujours une erreur 404, vous devez [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Passez à l’ [étape 10](#step-10).

+++

## Etape 10 - Vérification du message d&#39;erreur {#step-10}

+++**Existe-t-il un message d’erreur généré par la tâche cron ?**

Exemple : dans la table `core_config_data`, l’erreur *Le fichier &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0 ne peut pas être supprimé*. Warning!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0?lang=en): No such file or directory*

a. OUI - Utilisez le correctif ACSD-50165 dans [Le fichier ne peut pas être supprimé. Warning!unlink : aucune erreur de fichier ou de répertoire de ce type de la part de l’administrateur](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md), attendez 24 heures pour que la tâche s’exécute à nouveau, puis réessayez.\
b. NO - Passez à l&#39;[étape 11](#step-11).

+++

## Étape 11 - Vérification de l’erreur Page Builder {#step-11}

+++**Y a-t-il une erreur provoquée par le Créateur de pages ?**

Exemple : `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. OUI - Utilisez le correctif MDVA-19391 dans [Common Advanced Reporting Con job errors sur Adobe Commerce](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-cron-job-errors-magento-commerce.md), attendez 24 heures pour que la tâche s’exécute à nouveau et réessayez.\
b. NO - [soumettez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Retour à l’étape 1](#step-1)
