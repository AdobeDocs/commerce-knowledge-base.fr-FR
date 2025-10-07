---
title: Résolution des problèmes de stockage de la base de données sur Adobe Commerce
description: Cet article est un outil de dépannage destiné aux clients Adobe Commerce rencontrant des problèmes avec les bases de données. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’utilitaire de dépannage. Selon vos symptômes et votre configuration, l'utilitaire de dépannage vous expliquera comment résoudre les problèmes d'espace et de configuration liés aux bases de données.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: aa4cfbceb745f1a06b8a8f9e93cbdebbc151458b
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# Résolution des problèmes de stockage de la base de données sur Adobe Commerce

Cet article est un outil de dépannage destiné aux clients Adobe Commerce rencontrant des problèmes avec les bases de données. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’utilitaire de dépannage. Selon vos symptômes et votre configuration, l&#39;utilitaire de dépannage vous expliquera comment résoudre les problèmes d&#39;espace et de configuration liés aux bases de données.

## Étape 1 : identifier le répertoire présentant un problème d’espace {#step-1}

+++**Avez-vous un problème de `/tmp` dû à un manque d&#39;espace ?**

Cela peut être indiqué par divers symptômes, notamment le montage `/tmp` saturé, l’arrêt du site ou l’impossibilité d’effectuer un SSH sur un nœud. Vous pouvez également rencontrer des erreurs telles que _Aucun espace restant sur l’appareil (28)_. Pour obtenir la liste des erreurs résultant du remplissage de `/tmp`, consultez Montage [/tmp complet](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

Ou avez-vous un problème de `/data/mysql` causé par un manque d&#39;espace ? Cela peut également être indiqué par divers symptômes, notamment une panne du site, l’incapacité des clients à ajouter des produits au panier, un échec de connexion à la base de données et des erreurs Galeria telles que _SQLSTATE\[08S01\] : échec de la liaison de communication : 1047 WSREP_. Pour obtenir la liste des erreurs résultant d’un espace disque [!DNL MySQL] faible, reportez-vous à la section [[!DNL MySQL] Espace disque faible sur Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27806).

Si vous ne savez pas si vous rencontrez un problème d’espace disque et que vous disposez d’un compte New Relic, accédez à la page [Hôtes de surveillance de l’infrastructure New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). À partir de là, cliquez sur l&#39;onglet **Stockage**, modifiez la liste déroulante **Graphiques affichés** de 5 à 20 résultats, et recherchez dans le tableau une utilisation élevée du disque dans le graphique ou le tableau % d&#39;utilisation du disque. Pour obtenir des instructions plus détaillées, consultez [Surveillance de l’infrastructure New Relic > Onglet Stockage]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Si vous ressentez l’un des symptômes décrits ci-dessus, vérifiez l’état de vos nœuds pour vous assurer que cela n’est pas dû à des problèmes de numéro de fichier. Pour ce faire, exécutez la commande suivante dans l’interface de ligne de commande/Terminal :\
`df -ih`

UIse% > 90% ?

a. OUI - Cela est dû au fait qu’il y a trop de fichiers. Examinez les étapes pour supprimer les fichiers en toute sécurité dans [Supprimer en toute sécurité les fichiers lorsqu’ils ne disposent pas d’espace disque, Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26889). Passez à l’[étape 2](#step-2) une fois ces étapes terminées. Pour demander de l’espace supplémentaire, [envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NON - Vérifiez l’espace. Exécutez `df -h | grep mysql` puis `df -h | grep tmp` dans l’interface de ligne de commande/Terminal pour vérifier l’utilisation de l’espace disque dans les répertoires `/tmp` et `/data/mysql`. Passez à [étape 3](#step-3).

+++

## Étape 2 - Vérification de l’espace disque {#step-2}

+++**Vérifier l’utilisation de l’espace disque ?**

Une fois que vous avez réduit le nombre de fichiers, exécutez `df -h | grep mysql` puis `df -h | grep tmp` dans l’interface de ligne de commande/Terminal pour vérifier l’utilisation de l’espace disque dans `/tmp` et `/data/mysql`. Utilise-t-on plus de 70 % pour les `/tmp` ou les `/data/mysql` ?

a. OUI - Passer à [étape 3](#step-3).
b. NON - Les requêtes peuvent épuiser l’espace de stockage disponible. Cela peut provoquer la panne du nœud, entraînant la suppression de la requête et des fichiers `tmp`. Examinez la sortie de l’`SHOW PROCESSLIST;` dans l’interface de ligne de commande [!DNL MySQL] pour rechercher les requêtes qui peuvent être à l’origine du problème. [Envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour demander plus d’espace.

+++

## Étape 3 - Identification du répertoire à utilisation élevée {#step-3}

+++**Quel répertoire a été utilisé à plus de 70 % ?**

Quel répertoire a été utilisé à plus de 70 % ? `/tmp` ou `/data/mysql` ?

>[!NOTE]
>
>Par défaut, la base de données tmpdir écrit dans `/tmp`. Pour vérifier que la configuration de votre base de données fonctionne toujours sur cette valeur par défaut, exécutez la commande suivante dans [!DNL MySQL] CLI : `SHOW VARIABLES LIKE "TMPDIR";` Si la propriété tmpdir de la base de données écrit toujours sur `/tmp`, la `/tmp` s’affiche dans la colonne Valeur .

a. `/tmp` - Passez à [étape 4](#step-4). \
b. `/data/mysql` - Passez à [étape 5](#step-5).

+++

## Étape 4 - Dépannage du montage /tmp complet {#step-4}

+++**Résolution des problèmes liés au montage /tmp complet**

[Dépannage du montage /tmp complet pour Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), faites défiler l’article et essayez les solutions et les bonnes pratiques. Exécutez ensuite `df -h | grep mysql` puis `df -h | grep tmp` dans l’interface de ligne de commande/Terminal pour vérifier l’utilisation de l’espace disque dans les répertoires `/tmp` et `/data/mysql`\
  &lt; 70 % utilisé ?

>[!NOTE]
>
>Les solutions de [Dépannage du montage /tmp complet pour Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) sont conçues pour les commerçants qui n’ont pas modifié les variables de la base de données tmpdir, qui écrit par défaut dans `/tmp`. Si vous avez modifié la valeur tmpdir, les instructions de la section [Dépannage du montage /tmp complet pour Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) n’aideront pas.

a. OUI - Vous avez résolu le problème. \
b. NON - [Envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), pour demander plus d’espace.

+++

## Étape 5 - Vérifier les valeurs par défaut {#step-5}

+++**Vérifier par défaut**

Il se peut que votre configuration de base de données ne soit plus à sa valeur par défaut d&#39;origine. Recherchez la configuration tmpdir de la base de données en exécutant dans l’interface de ligne de commande [!DNL MySQL] : `SELECT @@DATADIR;`. Si `/data/mysql/` est généré, la base de données tmpdir écrit désormais dans `/data/mysql/`. Essayez d’augmenter l’espace dans ce répertoire en suivant les étapes décrites dans la section [[!DNL MySQL]  L’espace disque est faible sur Adobe Commerce sur notre infrastructure cloud](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27806). Exécutez ensuite `df -h | grep mysql` puis `df -h | grep tmp` dans l’interface de ligne de commande/Terminal pour vérifier l’utilisation de l’espace disque dans `/data/mysql` et `/tmp`.\
  &lt; 70 % utilisé ?

a. OUI - Vous avez résolu le problème. \
b. NON - [Envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), pour demander plus d’espace.

+++

[Retour à l’étape 1](#step-1)

## Lecture connexe

* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
