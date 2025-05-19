---
title: Résolution des problèmes liés au site Adobe Commerce
description: Cliquez sur chaque question pour afficher les détails des réponses à chaque étape de l’utilitaire de dépannage.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 66ff85507ec91def7aa836469b243c32c4e161cc
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Résolution des problèmes liés au site Adobe Commerce

Cliquez sur chaque question pour afficher les détails des réponses à chaque étape de l’utilitaire de dépannage.

>[!NOTE]
>
>Avant de créer un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide?lang=en#support-cases), consultez la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) pour voir si votre problème est déjà répertorié.

## Étape 1 {#step-1}

+++**Des problèmes apparaissent-<https://status.adobe.com> ?**

a. OUI - Si vous avez vérifié le statut [Adobe Commerce](https://status.adobe.com/cloud/experience_cloud) et qu’il a détecté un problème, ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) pour plus d’informations.\
b. NON - Si vous avez coché [Statut Adobe Commerce](https://status.adobe.com/cloud/experience_cloud) et qu’il n’a pas rencontré de problème, passez à [Étape 2](#step-2).

+++

## Étape 2 {#step-2}

+++**Y a-t-il des problèmes sur http://status.fastly.com ?**

a. OUI - Si vous avez coché la case [[!DNL Fastly] Statut](https://status.fastly.com/) et qu’elle indique un problème, ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) pour plus d’informations.\
b. NON - Si vous avez coché [[!DNL Fastly] Statut](https://status.fastly.com/) et qu’aucun problème ne s’est produit, passez à l’[étape 3](#step-3).

+++

## Étape 3 {#step-3}

+++**Consultez votre site web dans un navigateur web. Obtenez-vous un code 200 (OK) ?**

Pour vérifier les codes d’erreur dans **Firefox** : cliquez sur l’icône **Ouvrir le menu** > **Développeur Web** > **Activer/désactiver les outils** > **Onglet Réseau** > **All** filter > **Status** colonne. Pour vérifier les codes d&#39;erreur dans **Chrome** : cliquez sur l&#39;icône **Ouvrir le menu** > **Plus d&#39;outils** > **Outils de développement** > **Onglet Réseau** > **Tous** filtre > **Status** colonne.

a. OUI - Ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) pour plus d’informations.\
b. NON - Passer à [étape 4](#step-4).

+++

## Étape 4 {#step-4}

+++**Quel code d’erreur de site web avez-vous reçu ?**

a. Code d’erreur 500 - Vérifiez le journal de `/var/log/platform/`. Si ces données ne vous présentent pas le problème, vous pouvez ouvrir un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) et inclure les informations de dépannage dont vous disposez à ce jour pour une enquête plus approfondie.

b. Code d’erreur 503 - Vérifier le journal de `var/reports`. Si ces données ne vous présentent pas le problème, vous pouvez ouvrir un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) et inclure les informations de dépannage dont vous disposez à ce jour pour une enquête plus approfondie.

c. Code d’erreur 404 - Exécutez la requête suivante : `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Si la requête renvoie une table, où `update_exists` valeur est « 0 », reportez-vous à l’article [Erreur 404 sur toutes les pages, storefront et Admin, en raison d’un problème d’évaluation du contenu](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue). Dans tous les autres cas, passez à [étape 5](#step-5).

d. Autres codes d’erreur - Passez à [étape 5](#step-5).

+++

## Étape 5 {#step-5}

+++**Votre site est-il lent ou présente-t-il une charge de serveur élevée, une charge CPU élevée, un traitement des requêtes lent ou des pannes dans [!DNL MySQL] ou Redis ?**

a. OUI - Suivez les étapes de la [Vérification des attaques DDOS à partir de l’interface de ligne de commande](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli).\
b. NON - Vérifiez les journaux de `/var/log/exception.log` et de `/var/log/deploy.log`, et si ces données ne vous présentent pas le problème, passez à l’[étape 6](#step-6).

+++

## Étape 6 {#step-6}

+++**Avez-vous des erreurs de déploiement ou un échec de déploiement ?**

a. OUI - Passer à [étape 13](#step-13).\
b. NON - Passer à [étape 7](#step-7).

+++

## Étape 7 {#step-7}

+++**Avez-vous des erreurs Elasticsearch ?**

a. OUI - Suivez les étapes de [vérification d’Elasticsearch](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/search/configure-search-engine).
b. NON - Passer à [étape 8](#step-8).

+++

## Étape 8 {#step-8}

+++**Votre base de données [!DNL MySQL] comportait-elle des requêtes lentes ou incorrectes ?**

a. OUI - Effectuez la [Vérification des requêtes lentes et des processus prenant trop de temps dans le tutoriel  [!DNL MySQL]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql) and checking your query structure in this [[!DNL MySQL]  requête](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NON - Passer à [étape 9](#step-9).

+++

## Étape 9 {#step-9}

+++**Votre contenu statique n’est-il pas disponible ?**

a. OUI - Consultez l’article [Vérification du contenu statique](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment).\
b. NON - Passer à [étape 10](#step-10).

+++

## Étape 10 {#step-10}

+++**Voyez-vous des erreurs fatales PHP dans vos logs ?**

a. OUI - Poursuivre la consultation [Erreurs courantes et solutions fatales PHP](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions).\
b. NON - Passer à [étape 11](#step-11).

+++

## Étape 11 {#step-11}

+++**Est-ce que vous voyez des erreurs Redis ?**

a. OUI - Suivez les étapes de [vérification [!DNL Redis] exécution](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection) et de [[!DNL Redis] dépannage](https://redis.io/topics/problems).\
b. NON - Passer à [étape 12](#step-12).

+++

## Étape 12 {#step-12}

+++**Est-ce que des erreurs d’indexeur s’affichent ?**

a. OUI - Si votre index est verrouillé par un autre processus, consultez [L’index est verrouillé par un autre processus](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/index-is-locked-by-another-process). Si vous rencontrez d’autres erreurs de l’indexeur, ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) pour plus d’informations.\
b. NON - Ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) pour plus d’informations.

+++

## Étape 13 {#step-13}

+++**Rencontrez-vous des problèmes avec votre ou vos modules personnalisés ?**

a. OUI - Procédez à une consultation [Aide générale pour le dépannage des modules personnalisés](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help).\
b. NON - Passer à [étape 14](#step-14).

+++

## Étape 14 {#step-14}

+++**Avez-vous des pannes de post-hook ?**

a. OUI - Effectuez la vérification de votre erreur [!DNL MySQL] dans cette [[!DNL MySQL] référence du message d’erreur du serveur](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NON - Passer à [étape 15](#step-15).

+++

## Étape 15 {#step-15}

+++**Avez-vous des problèmes avec les correctifs du compositeur ?**

a. OUI - Passer à la consultation [L’application d’un correctif entraîne l’arrêt de votre site](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down).\
b. NON - Passer à [étape 16](#step-16).

+++

## Étape 16 {#step-16}

+++**Avez-vous des erreurs de base de données SQL ?**

a. OUI - Effectuez la vérification de votre erreur [!DNL MySQL] dans cette [[!DNL MySQL] référence du message d’erreur du serveur](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NON - Passer à [étape 17](#step-17).

+++

## Étape 17 {#step-17}

+++**Avez-vous [!DNL MySQL] base de données bloquée ou une base de données [!DNL MySQL] qui ne répond pas ?**

a. OUI - Effectuez la vérification des interblocages [!DNL MySQL] dans cet article [Interblocages dans [!DNL MySQL]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/database/deadlocks-in-mysql).\
b. NON - Ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) pour plus d’informations.

+++

[Retour à l’étape 1](#step-1)

Cliquez [ICI](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram) pour voir l&#39;organigramme de dépannage du site.

## Lecture connexe

[Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
