---
title: Résolution des problèmes liés aux rapports avancés pour Adobe Commerce
description: Les problèmes de création de rapports avancés sur Adobe Commerce peuvent être résolus à l’aide de cet outil de dépannage. Cela inclut les rapports avancés qui n’affichent aucune donnée et les erreurs 404. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’utilitaire de dépannage.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 842c329b5d8bacf72ac689412fde5a5d76d16e85
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 0%

---

# Résolution des problèmes liés aux rapports avancés pour Adobe Commerce

Les problèmes de création de rapports avancés sur Adobe Commerce peuvent être résolus à l’aide de cet outil de dépannage. Cela inclut les rapports avancés qui n’affichent aucune donnée et les erreurs 404. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’utilitaire de dépannage.

## Étape 1 - Confirmer que le site répond aux exigences de création de rapports avancées {#step-1}

+++**Votre site web répond-il aux exigences de reporting avancé ?**

Une page d’erreur 404 s’affiche lors de l’utilisation des rapports avancés. Votre site web répond-il aux [exigences de reporting avancé](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements) ?

a. OUI - Passer à [étape 2](#step-2).\
b. NON - Renseignez les exigences de création de rapports avancés pour votre site en suivant les étapes indiquées dans [ Exigences de création de rapports avancés ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements). Passez ensuite à [Étape 2](#step-2).

+++

## Etape 2 - Y a-t-il des commandes dans plusieurs devises de base ? {#step-2}

+++**Plusieurs devises de base sont-elles utilisées ?**

Plusieurs devises de base sont-elles utilisées (dans les commandes et la configuration) ? Exécutez la commande [!DNL SQL] pour obtenir la configuration actuelle : `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. OUI - Si la requête renvoie plusieurs lignes, vous ne pouvez pas utiliser la création de rapports avancée, car nous ne prenons en charge qu’une seule devise.\
b. NON - La sortie n’affiche qu’une seule devise. Exemple : `USD`. Plusieurs devises de base ont-elles déjà été utilisées (dans les commandes) ? Exécutez cette commande [!DNL SQL] pour obtenir les données des commandes historiques :\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**REMARQUE : cette commande nécessite une analyse complète des tables. Par conséquent, pour les tables comportant un grand nombre d&#39;enregistrements, cela peut avoir un impact sur les performances pendant l&#39;exécution de la requête** afin d&#39;obtenir les données des ordres historiques.
Si plusieurs devises de base ont déjà été utilisées, vous ne pouvez pas utiliser les rapports avancés, car nous ne prenons en charge qu&#39;une seule devise. Si la sortie n’affiche qu’une seule devise, passez à [étape 3](#step-3).

+++

## Étape 3 : vérifier si la base de données fractionnée est utilisée {#step-3}

+++**Utilisez-vous une solution de base de données partagée ?**

Utilisez-vous [solution de base de données partagée](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master) ?

a. OUI - Utilisez le correctif **MDVA-26831** dans Advanced Reporting 404 - Erreur sur la solution de base de données partagée et effacez le cache. Patientez 24 heures pour que le traitement s’exécute à nouveau et réessayez.\
b. NON - Passer à [étape 4](#step-4).

+++

## Étape 4 - Confirmer la création de rapports avancés activée {#step-4}

+++**Les rapports avancés sont-ils activés ?**

Cochez **Admin** > **Magasins** > **Paramètres** > **Configuration** > **Général** > **Rapports avancés**. Pour obtenir des instructions détaillées, consultez [Rapports avancés : activer les rapports avancés](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting).

a. OUI - Passer à [étape 5](#step-5).\
b. NON - [Activer la création de rapports avancée](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) et enregistrez-les, puis attendez 24 heures pour qu’Adobe Commerce et la création de rapports avancée se synchronisent. Vérifiez si vos données se chargent maintenant. Si c&#39;est le cas, vous avez résolu le problème. S’il ne passe pas à l’[étape 5](#step-5).

+++

## Étape 5 - Vérifier le jeton {#step-5}

+++**Existe-t-il un jeton ?**

Vérifiez qu’il existe un jeton en exécutant la requête suivante : `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` Existe-t-il un jeton ?

a. OUI - Passer à [étape 7](#step-7).\
b. NON - Si la valeur du jeton est NULL ou s’il n’existe aucun enregistrement dans la base de données, passez à l’[étape 6](#step-6).

+++

## Étape 6 - Utiliser la ligne {#step-6}

+++**La requête renvoie-t-elle la ligne ?**

Vérifiez la valeur du compteur dans la table des indicateurs en exécutant cette requête : ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` La requête renvoie-t-elle la ligne ?

a. OUI - Prendre les mesures suivantes : 1. Exécutez la requête ci-dessous :\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\ [Désactivez et activez le module Rapports avancés](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) dans les paramètres et [réautorisez le jeton](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
3\ Patientez 24 heures pour qu’Adobe Commerce et les rapports avancés se synchronisent. Si vous ne pouvez toujours pas voir les données dans les rapports avancés, [envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NON - Si la requête ne renvoie rien, procédez comme suit : 1. [Désactivez et activez le module Rapports avancés](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) dans les paramètres et [réautorisez le jeton](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
2\ Patientez 24 heures pour qu’Adobe Commerce et les rapports avancés se synchronisent. Si vous ne pouvez toujours pas voir les données dans les rapports avancés, [envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Étape 7 - Rechercher des enregistrements dans `cron_schedule` table {#step-7}

+++**Y a-t-il des enregistrements dans la table `cron_schedule` ?**

Vérifiez que le traitement `analytics_collect_data` été exécuté en exécutant cette requête : `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. OUI - S’il existe des enregistrements et que la colonne **statut** indique _manqué_, utilisez le correctif de cet article de la base de connaissances pour mettre à jour les rapports avancés et exécuter sur son propre groupe cron.\
b. OUI - S’il existe des enregistrements et que la colonne **statut** indique _succès_, passez à [étape 9](#step-9).\
c. OUI - S’il existe des enregistrements et que la colonne **statut** indique _erreur_, passez à l’[étape 8.](#step-8)\
d. NON - S’il n’y a aucun enregistrement, passez à [étape 8](#step-8).

+++

## Étape 8 - Rechercher un travail dans `support_report.log` {#step-8}

+++**Le traitement était-il connecté `support_report.log` ?**

Exécutez la commande : `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. OUI - Si la sortie de la requête indique une tâche réussie, par exemple `Cron Job analytics_collect_data is successfully finished` passez à l’[étape 9](#step-9).\
b. NON - S’il n’y a aucun enregistrement dans le journal, [soumettez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. OUI - S’il y a des enregistrements, mais qu’il y a une erreur, passez à l’[étape 10](#step-10).

+++

## Étape 9 - Vérifier le fichier `data.tgz` {#step-9}

+++**Le `data.tgz` de fichiers existe-t-il dans le système et existe-t-il des enregistrements dans les journaux d’accès ?**

Pour vérifier que le fichier `data.tgz` existe, exécutez cette commande - elle doit renvoyer le ou les répertoires avec le ou les noms de hachage :

```
ls -ltr pub/media/analytics/
```

Pour vérifier qu’il existe des enregistrements dans access.logs, exécutez la commande suivante :

* Sous Commerce Cloud :

  ```
  {{zgrep -i analytics /var/log/platform/*/access.log* | grep MagentoBI}}
  ```

* Pour On-Premise, remplacez le chemin d’accès au fichier en conséquence :
  `zgrep -i analytics <your web server's log path>/access.log* | grep MagentoBI`

a. OUI - Si le fichier `data.tgz` est présent et qu’il existe des enregistrements dans les journaux d’accès, mais que vous rencontrez toujours une erreur 404, vous devez [soumettre un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NON - Passer à [étape 10](#step-10).

+++

## Étape 10 - Vérifier le message d’erreur {#step-10}

+++**La tâche cron renvoie-t-elle un message d’erreur ?**

Exemple : dans le tableau `cron_schedule`, l’erreur *Le fichier « /app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0 ne peut pas être supprimé* s’affiche. Avertissement!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0?lang=fr) : aucun fichier ou répertoire de ce type*

a. OUI - Utilisez le correctif ACSD-50165 dans [Le fichier ne peut pas être supprimé. Avertissement!unlink : aucune erreur de fichier ou de répertoire de ce type de la part de l’administrateur](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26887), attendez 24 heures pour que le traitement s’exécute à nouveau, puis réessayez.\
b. NON - Passer à [étape 11](#step-11).

+++

## Étape 11 - Vérifier s’il existe une erreur Page Builder {#step-11}

+++**Une erreur est-elle due à Page Builder ?**

Exemple : `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. OUI - Utilisez le correctif MDVA-19391 dans Erreurs de tâche cron de rapports avancés courants sur Adobe Commerce, attendez 24 heures que la tâche s’exécute à nouveau et réessayez.\
b. NON - [soumettez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Retour à l’étape 1](#step-1)

## Lecture connexe

[Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
