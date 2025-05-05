---
title: Dépannage du site Adobe Commerce
description: Cliquez sur chaque question pour afficher les détails de la réponse à chaque étape de l’outil de dépannage.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 0%

---

# Dépannage du site Adobe Commerce

Cliquez sur chaque question pour afficher les détails de la réponse à chaque étape de l’outil de dépannage.

## Étape 1 {#step-1}

+++**<https://status.adobe.com> présente-t-il des problèmes ?**

a. OUI - Si vous avez coché [Statut Adobe Commerce](https://status.adobe.com/cloud/experience_cloud) et qu’un problème s’est produit, ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) pour plus d’informations.\
b. NON - Si vous avez coché [État Adobe Commerce](https://status.adobe.com/cloud/experience_cloud) et qu’il n’y a pas eu de problème, passez à l’ [Étape 2](#step-2).

+++

## Étape 2 {#step-2}

+++**http://status.fastly.com affiche-t-il des problèmes ?**

a. OUI - Si vous avez coché [[!DNL Fastly] Status](https://status.fastly.com/) et qu’un problème s’est produit, ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) pour plus d’informations.\
b. NO - Si vous avez coché [[!DNL Fastly] Status](https://status.fastly.com/) et qu&#39;il n&#39;y a pas de problème, passez à l&#39;[Étape 3](#step-3).

+++

## Étape 3 {#step-3}

+++**Consultez votre site web dans un navigateur web. Avez-vous un code 200 (OK) ?**

Pour vérifier les codes d’erreur dans **Firefox** : cliquez sur l’icône **Open Menu** > **Web Developer** > **Toggle Tools** > **Network** > **All** filter > **Status** column. Pour vérifier les codes d’erreur dans **Chrome** : cliquez sur l’icône **Ouvrir le menu** > **Plus d’outils** > **Outils de développement** > **Onglet Réseau** > **Filtre All** > Colonne **État**.

a. OUI - Ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) pour plus d’informations.\
b. NO - Passez à [Étape 4](#step-4).

+++

## Étape 4 {#step-4}

+++**Quel code d’erreur de site web avez-vous reçu ?**

a. Code d’erreur 500 - Vérifier le journal de `/var/log/platform/`. Si ces données ne vous présentent pas le problème, vous pouvez ouvrir un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) et inclure les informations de dépannage dont vous disposez jusqu’à présent pour plus d’informations.

b. Code d’erreur 503 - Vérifier le journal de `var/reports`. Si ces données ne vous présentent pas le problème, vous pouvez ouvrir un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) et inclure les informations de dépannage dont vous disposez jusqu’à présent pour plus d’informations.

c. Code d’erreur 404 - Exécutez la requête suivante : `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Si la requête renvoie une table, où la valeur `update_exists` est &quot;0&quot;, reportez-vous à l’article [Erreur 404 sur toutes les pages, storefront et Admin, en raison d’un problème d’évaluation de contenu](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue). Dans tous les autres cas, passez à l&#39;[étape 5](#step-5).

d. Autres codes d’erreur - Passez à l’ [étape 5](#step-5).

+++

## Étape 5 {#step-5}

+++**Votre site est-il lent ou son serveur est-il très chargé, charge importante du processeur, traitement lent des requêtes ou panne dans [!DNL MySQL] ou Redis ?**

a. OUI - Passez à la procédure [Vérification des attaques DDOS de l’interface de ligne de commande](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli).\
b. NO - Vérifiez les journaux de `/var/log/exception.log` et `/var/log/deploy.log`, et si ces données ne vous présentent pas le problème, passez à l&#39;[étape 6](#step-6).

+++

## Étape 6 {#step-6}

+++**Avez-vous des erreurs de déploiement ou un échec de déploiement ?**

a. OUI - Passez à l’[étape 13](#step-13).\
b. NO - Passez à l’ [étape 7](#step-7).

+++

## Étape 7 {#step-7}

+++**Y a-t-il des erreurs de l’Elasticsearch ?**

a. OUI - Passez à la procédure de [vérification d’Elasticsearch](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/search/configure-search-engine).
b. NO - Passez à [Étape 8](#step-8).

+++

## Étape 8 {#step-8}

+++**Votre base de données [!DNL MySQL] contenait-elle des requêtes lentes ou incorrectes ?**

a. OUI - Poursuivez en [vérifiant que les requêtes et les processus lents prennent trop de temps dans le  [!DNL MySQL]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql) and checking your query structure in this [[!DNL MySQL] tutoriel sur les requêtes](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NO - Passez à [Étape 9](#step-9).

+++

## Étape 9 {#step-9}

+++**Votre contenu statique n’est-il pas disponible ?**

a. OUI - Continuez avec la consultation de l&#39;article [Vérification du contenu statique](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment) .\
b. NO - Passez à l’ [étape 10](#step-10).

+++

## Étape 10 {#step-10}

+++**Vous voyez des erreurs fatales PHP dans vos logs ?**

a. OUI - Continuez avec le service de conseil [Erreurs et solutions fatales PHP courantes](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions).\
b. NO - Passez à l&#39;[étape 11](#step-11).

+++

## Étape 11 {#step-11}

+++**Vous voyez des erreurs Redis ?**

a. OUI - Passez à la procédure [verify [!DNL Redis] est en cours d’exécution](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection) et pour [[!DNL Redis] la résolution des problèmes](https://redis.io/topics/problems).\
b. NO - Passez à l&#39;[étape 12](#step-12).

+++

## Étape 12 {#step-12}

+++**Vous voyez des erreurs de l’indexeur ?**

a. OUI - Si votre index est verrouillé par un autre processus, consultez [L&#39;index est verrouillé par un autre processus](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/index-is-locked-by-another-process). Si vous rencontrez d’autres erreurs de l’indexeur, ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) pour plus d’informations.\
b. NO - Ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) pour plus d’informations.

+++

## Étape 13 {#step-13}

+++**Vous avez des problèmes avec votre ou vos modules personnalisés ?**

a. OUI - Passez à la [Aide générale de dépannage des modules personnalisés](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help).\
b. NO - Passez à l&#39;[étape 14](#step-14).

+++

## Étape 14 {#step-14}

+++**Avez-vous des échecs post-hook ?**

a. OUI - Continuez en vérifiant votre erreur [!DNL MySQL] dans cette [[!DNL MySQL] référence de message d’erreur du serveur](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Passez à l’ [étape 15](#step-15).

+++

## Étape 15 {#step-15}

+++**Vous avez des problèmes avec les correctifs de compositeur ?**

a. OUI - Passez à la consultation [L’application d’un correctif réduit votre site](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down).\
b. NO - Passez à l&#39;[étape 16](#step-16).

+++

## Étape 16 {#step-16}

+++**Avez-vous des erreurs de base de données SQL ?**

a. OUI - Continuez en vérifiant votre erreur [!DNL MySQL] dans cette [[!DNL MySQL] référence de message d’erreur du serveur](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Passez à l&#39;[étape 17](#step-17).

+++

## Étape 17 {#step-17}

+++**Avez-vous des [!DNL MySQL] verrous morts de la base de données ou une base de données [!DNL MySQL] non réactive ?**

a. OUI - Poursuivez la vérification des [!DNL MySQL] blocages dans cet article [Deadlocks in [!DNL MySQL]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/database/deadlocks-in-mysql) .\
b. NO - Ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) pour plus d’informations.

+++

[Retour à l’étape 1](#step-1)

Cliquez sur [HERE](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram) pour afficher l’organigramme de dépannage du site vers le bas.

## Lecture connexe

[ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
