---
title: Dépannage du site Adobe Commerce
description: Cliquez sur chaque question pour afficher les détails de la réponse à chaque étape de l’outil de dépannage.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Dépannage du site Adobe Commerce

Cliquez sur chaque question pour afficher les détails de la réponse à chaque étape de l’outil de dépannage.

## Étape 1 {#step-1}

+++**<https://status.adobe.com> présente-t-il des problèmes ?**

a. OUI - Si vous avez coché [Adobe Magento Status](https://status.adobe.com/products/3350) et qu’un problème s’est produit, ouvrez un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour plus d’informations.\
b. NO - Si vous avez coché [Adobe Magento Status](https://status.adobe.com/products/3350) et qu’il n’y a pas de problème, passez à l’ [étape 2](#step-2).

+++

## Étape 2 {#step-2}

+++**http://status.fastly.com affiche-t-il des problèmes ?**

a. OUI - Si vous avez coché [État Fastly](https://status.fastly.com/) et qu’un problème s’est produit, ouvrez un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour plus d’informations.\
b. NO - Si vous avez coché [Fastly Status](https://status.fastly.com/) et qu’il n’y a pas de problème, passez à l’ [Étape 3](#step-3).

+++

## Étape 3 {#step-3}

+++**Consultez votre site web dans un navigateur web. Avez-vous un code 200 (OK) ?**

Pour vérifier les codes d’erreur dans **Firefox** : cliquez sur l’icône **Open Menu** > **Web Developer** > **Toggle Tools** > **Network** > **All** filter > **Status** column. Pour vérifier les codes d’erreur dans **Chrome** : cliquez sur l’icône **Ouvrir le menu** > **Plus d’outils** > **Outils de développement** > **Onglet Réseau** > **Filtre All** > Colonne **État**.

a. OUI - Ouvrez un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour plus d’informations.\
b. NO - Passez à [Étape 4](#step-4).

+++

## Étape 4 {#step-4}

+++**Quel code d’erreur de site web avez-vous reçu ?**

a. Code d’erreur 500 - Vérifier le journal de `/var/log/platform/`. Si ces données ne vous présentent pas le problème, vous pouvez ouvrir un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) et inclure les informations de dépannage dont vous disposez jusqu’à présent pour plus d’informations.

b. Code d’erreur 503 - Vérifier le journal de `var/reports`. Si ces données ne vous présentent pas le problème, vous pouvez ouvrir un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) et inclure les informations de dépannage dont vous disposez jusqu’à présent pour plus d’informations.

c. Code d’erreur 404 - Exécutez la requête suivante : `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Si la requête renvoie une table, où la valeur `update_exists` est &quot;0&quot;, reportez-vous à l’article [Erreur 404 sur toutes les pages, storefront et Admin, en raison d’un problème d’évaluation de contenu](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md). Dans tous les autres cas, passez à l&#39;[étape 5](#step-5).

d. Autres codes d’erreur - Passez à l’ [étape 5](#step-5).

+++

## Étape 5 {#step-5}

+++**Votre site est-il lent ou son serveur est-il trop chargé, le processeur est trop chargé, le traitement des requêtes trop lent ou les pannes dans MySQL ou Redis ?**

a. OUI - Passez à la procédure [Vérification des attaques DDOS de l’interface de ligne de commande](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md).\
b. NO - Vérifiez les journaux de `/var/log/exception.log` et `/var/log/deploy.log`, et si ces données ne vous présentent pas le problème, passez à l&#39;[étape 6](#step-6).

+++

## Étape 6 {#step-6}

+++**Avez-vous des erreurs de déploiement ou un échec de déploiement ?**

a. OUI - Passez à l’[étape 13](#step-13).\
b. NO - Passez à l’ [étape 7](#step-7).

+++

## Étape 7 {#step-7}

+++**Y a-t-il des erreurs de l’Elasticsearch ?**

a. OUI - Passez à la procédure de [vérification d’Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html).\
b. NO - Passez à [Étape 8](#step-8).

+++

## Étape 8 {#step-8}

+++**Votre base de données MySQL comportant des requêtes lentes ou incorrectes ?**

a. OUI - Poursuivez en [vérifiant que les requêtes et les processus lents prennent trop de temps dans MySQL](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md) et en vérifiant la structure de vos requêtes dans ce [tutoriel sur les requêtes MySQL](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NO - Passez à [Étape 9](#step-9).

+++

## Étape 9 {#step-9}

+++**Votre contenu statique n’est-il pas disponible ?**

a. OUI - Continuez avec la consultation de l&#39;article [Vérification du contenu statique](https://support.magento.com/hc/en-us/articles/360031624091) .\
b. NO - Passez à l’ [étape 10](#step-10).

+++

## Étape 10 {#step-10}

+++**Vous voyez des erreurs fatales PHP dans vos logs ?**

a. OUI - Continuez avec le service de conseil [Erreurs et solutions fatales PHP courantes](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md).\
b. NO - Passez à l&#39;[étape 11](#step-11).

+++

## Étape 11 {#step-11}

+++**Vous voyez des erreurs Redis ?**

a. OUI - Passez à la [vérification que Redis est en cours d’exécution](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify) et pour la [résolution des problèmes de Redis](https://redis.io/topics/problems).\
b. NO - Passez à l&#39;[étape 12](#step-12).

+++

## Étape 12 {#step-12}

+++**Vous voyez des erreurs de l’indexeur ?**

a. OUI - Si votre index est verrouillé par un autre processus, consultez [L&#39;index est verrouillé par un autre processus](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md). Si vous rencontrez d’autres erreurs de l’indexeur, ouvrez un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour plus d’informations.\
b. NO - Ouvrez un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour plus d’informations.

+++

## Étape 13 {#step-13}

+++**Vous avez des problèmes avec votre ou vos modules personnalisés ?**

a. OUI - Passez à la [Aide générale de dépannage des modules personnalisés](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md).\
b. NO - Passez à l&#39;[étape 14](#step-14).

+++

## Étape 14 {#step-14}

+++**Avez-vous des échecs post-hook ?**

a. OUI - Continuez en vérifiant votre erreur MySQL dans cette [référence de message d’erreur du serveur MySQL](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Passez à l’ [étape 15](#step-15).

+++

## Étape 15 {#step-15}

+++**Vous avez des problèmes avec les correctifs de compositeur ?**

a. OUI - Passez à la consultation [L’application d’un correctif réduit votre site](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md).\
b. NO - Passez à l&#39;[étape 16](#step-16).

+++

## Étape 16 {#step-16}

+++**Avez-vous des erreurs de base de données SQL ?**

a. OUI - Continuez en vérifiant votre erreur MySQL dans cette [référence de message d’erreur du serveur MySQL](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Passez à l&#39;[étape 17](#step-17).

+++

## Étape 17 {#step-17}

+++**Avez-vous des verrous morts de la base de données MySQL ou une base de données MySQL non réactive ?**

a. OUI - Poursuivez la vérification des verrous morts MySQL dans cet article [Deadlocks in MySQL](/help/troubleshooting/database/deadlocks-in-mysql.md) .\
b. NO - Ouvrez un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour plus d’informations.

+++

[Retour à l’étape 1](#step-1)

Cliquez sur [HERE](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md) pour afficher l’organigramme de dépannage du site vers le bas.
