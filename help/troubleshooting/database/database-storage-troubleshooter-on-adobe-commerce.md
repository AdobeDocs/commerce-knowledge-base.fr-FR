---
title: Résolution des problèmes de stockage dans la base de données sur Adobe Commerce
description: Cet article est un outil de dépannage pour les clients d’Adobe Commerce qui rencontrent des problèmes avec les bases de données. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’outil de dépannage. Selon vos symptômes et votre configuration, l’outil de dépannage explique comment résoudre les problèmes d’espace et de configuration avec les bases de données.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Résolution des problèmes de stockage dans la base de données sur Adobe Commerce

Cet article est un outil de dépannage pour les clients d’Adobe Commerce qui rencontrent des problèmes avec les bases de données. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’outil de dépannage. Selon vos symptômes et votre configuration, l’outil de dépannage explique comment résoudre les problèmes d’espace et de configuration avec les bases de données.

## Étape 1 - Identifier le répertoire avec un problème d’espace {#step-1}

+++**Avez-vous un `/tmp` un problème causé par un manque d&#39;espace ?**

Cela peut être indiqué par une série de symptômes, dont le `/tmp` le montage étant plein, le site vers le bas ou ne pouvant pas se connecter à SSH dans un noeud. Vous pouvez également rencontrer des erreurs telles que _Aucun espace laissé sur l’appareil (28)_. Pour une liste des erreurs résultant de `/tmp` être complet, révision [/tmp montage full](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

Ou avez-vous un `/data/mysql` un problème causé par un manque d&#39;espace ? Cela peut également être indiqué par divers symptômes, dont une panne du site, des clients incapables d’ajouter des produits au panier, un échec de connexion à la base de données et des erreurs Galeria, comme _SQLSTATE\[08S01\] : Échec du lien de communication : 1047 WSREP_. Pour une liste des erreurs résultant d&#39;un faible espace disque MySQL, reportez-vous à la section [L’espace disque MySQL est faible sur Adobe Commerce sur l’infrastructure cloud](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

Si vous ne savez pas si vous rencontrez un problème d’espace disque et que vous disposez d’un compte New Relic, accédez à la [Page d’hôtes de surveillance de l’infrastructure New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). À partir de là, cliquez sur le **Stockage** , modifiez la variable **Affichage du graphique** faites une liste déroulante de 5 à 20 résultats, puis recherchez dans le tableau l’utilisation élevée du disque dans le graphique ou le tableau % utilisé par le disque . Pour obtenir des instructions plus détaillées, voir [Surveillance de l’infrastructure New Relic > onglet Stockage]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Si vous avez l’un des symptômes décrits ci-dessus, vérifiez l’état de vos inodes pour vous assurer que cela n’est pas dû à des problèmes de numéro de fichier. Pour ce faire, exécutez la commande suivante dans l’interface de ligne de commande/le terminal :\
`df -ih`

UIse% > 90% ?

a. OUI - Cela est dû à un trop grand nombre de fichiers. Examinez les étapes de suppression des fichiers en toute sécurité dans . [Suppression sécurisée de fichiers en cas de manque d’espace disque, Adobe Commerce sur l’infrastructure cloud](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). Passez à [Étape 2](#step-2) une fois ces étapes terminées. Si vous souhaitez demander plus d’espace, [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NON - Vérifier l’espace. Exécuter `df -h | grep mysql` puis `df -h | grep tmp` dans l’interface en ligne de commande/le terminal pour vérifier l’utilisation de l’espace disque dans la variable `/tmp` et `/data/mysql` répertoires. Passez à [Étape 3](#step-3).

+++

## Etape 2 - Vérifier l&#39;espace disque {#step-2}

+++**Vérifiez l’utilisation de l’espace disque ?**

Une fois le nombre de fichiers réduit, exécutez `df -h | grep mysql` puis `df -h | grep tmp` dans l’interface en ligne de commande/le terminal pour vérifier l’utilisation de l’espace disque dans `/tmp` et `/data/mysql`. Est supérieur à 70 % utilisé pour `/tmp` ou `/data/mysql`?

a. OUI - Passez à [Étape 3](#step-3).
b. NO - Les requêtes peuvent épuiser le stockage disponible. Cela peut entraîner un blocage du noeud, ce qui tue la requête et supprime la variable `tmp` fichiers . Examiner la sortie de la variable `SHOW PROCESSLIST;` dans l’interface de ligne de commande MySQL pour les requêtes qui peuvent être la cause du problème. [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), demandant plus d’espace.

+++

## Étape 3 - Identifier le répertoire avec une utilisation élevée {#step-3}

+++**Quel répertoire utilise plus de 70 % ?**

Quel répertoire utilise plus de 70 % ? `/tmp` ou `/data/mysql`?

>[!NOTE]
>
>Par défaut, tmpdir de base de données écrit sur `/tmp`. Pour vérifier que la configuration de votre base de données est toujours sur cette valeur par défaut, exécutez la commande suivante dans l’interface de ligne de commande MySQL : `SHOW VARIABLES LIKE "TMPDIR";` Si le tmpdir de la base de données est toujours en train d’écrire vers `/tmp`, `/tmp` dans la colonne Valeur .

a. `/tmp` - Passez à [Étape 4](#step-4). \
b. `/data/mysql` - Passez à [Étape 5](#step-5).

+++

## Étape 4 - Dépannage du montage /tmp complet {#step-4}

+++**Dépannage /tmp de la version complète**

[Résolution des problèmes /tmp de montage complet pour Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), faites défiler l’article vers le bas et essayez les solutions et les bonnes pratiques. Exécutez ensuite `df -h | grep mysql` puis `df -h | grep tmp` dans l’interface en ligne de commande/le terminal pour vérifier l’utilisation de l’espace disque dans `/tmp` et `/data/mysql` répertoires\
  &lt; 70 % utilisé ?

>[!NOTE]
>
>Les solutions dans [Résolution des problèmes /tmp de montage complet pour Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) sont conçus pour les marchands qui n’ont pas modifié les variables de la base de données tmpdir, qui écrit par défaut sur `/tmp`. Si vous avez modifié la valeur de tmpdir, suivez les instructions de la section [Résolution des problèmes /tmp de montage complet pour Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) ne vous aidera pas.

a. OUI - Vous avez résolu le problème. \
b. NON - [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), demandant plus d’espace.

+++

## Étape 5 - Vérifier la valeur par défaut {#step-5}

+++**Vérifier par défaut**

Il se peut que la configuration de votre base de données ne soit plus celle par défaut d’origine. Recherchez la configuration tmpdir de base de données en exécutant dans l’interface de ligne de commande MySQL : `SELECT @@DATADIR;`. If `/data/mysql/` est généré, la base de données tmpdir est maintenant en train d’écrire vers `/data/mysql/`. Essayez d’augmenter l’espace dans ce répertoire en suivant les étapes de la section [L’espace disque MySQL est faible sur Adobe Commerce sur notre infrastructure cloud](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). Exécutez ensuite `df -h | grep mysql` puis `df -h | grep tmp` dans l’interface en ligne de commande/le terminal pour vérifier l’utilisation de l’espace disque dans `/data/mysql` et `/tmp`.\
  &lt; 70 % utilisé ?

a. OUI - Vous avez résolu le problème. \
b. NON - [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), demandant plus d’espace.

+++

[Retour à l’étape 1](#step-1)
