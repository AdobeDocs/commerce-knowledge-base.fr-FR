---
title: Résolution des problèmes de stockage dans la base de données sur Adobe Commerce
description: Cet article est un outil de dépannage pour les clients d’Adobe Commerce qui rencontrent des problèmes avec les bases de données. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’outil de dépannage. Selon vos symptômes et votre configuration, l’outil de dépannage explique comment résoudre les problèmes d’espace et de configuration avec les bases de données.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Résolution des problèmes de stockage dans la base de données sur Adobe Commerce

Cet article est un outil de dépannage pour les clients d’Adobe Commerce qui rencontrent des problèmes avec les bases de données. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’outil de dépannage. Selon vos symptômes et votre configuration, l’outil de dépannage explique comment résoudre les problèmes d’espace et de configuration avec les bases de données.

## Étape 1 - Identifier le répertoire avec un problème d’espace {#step-1}

+++**Avez-vous un problème `/tmp` causé par un manque d&#39;espace ?**

Cela peut être indiqué par une série de symptômes, dont le montage `/tmp` étant plein, le site en panne ou ne pouvant pas se SSH dans un noeud. Vous pouvez également rencontrer des erreurs telles que _Aucun espace laissé sur l’appareil (28)_. Pour obtenir une liste des erreurs résultant de l’saturation de `/tmp`, consultez [/tmp montage full](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

Ou avez-vous un problème `/data/mysql` causé par un manque d&#39;espace ? Cela peut également être indiqué par divers symptômes, dont une panne du site, des clients qui ne peuvent pas ajouter de produits au panier, un échec de connexion à la base de données et des erreurs Galeria, telles que _SQLSTATE\[08S01\] : échec du lien de communication : 1047 WSREP_. Pour une liste des erreurs résultant d&#39;un faible espace disque [!DNL MySQL], reportez-vous à la section [[!DNL MySQL] l&#39;espace disque est faible sur Adobe Commerce sur l&#39;infrastructure cloud](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

Si vous ne savez pas si vous rencontrez un problème d’espace disque et que vous disposez d’un compte New Relic, accédez à la [page Hôtes de surveillance de l’infrastructure New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). À partir de là, cliquez sur l’onglet **Stockage**, modifiez la liste déroulante **Afficher le graphique** de 5 à 20 résultats, puis recherchez dans le tableau une utilisation élevée du disque dans le graphique ou le tableau % utilisé par le disque. Pour obtenir des instructions plus détaillées, reportez-vous à la section [Surveillance de l’infrastructure New Relic > Onglet Stockage]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Si vous avez l’un des symptômes décrits ci-dessus, vérifiez l’état de vos inodes pour vous assurer que cela n’est pas dû à des problèmes de numéro de fichier. Pour ce faire, exécutez la commande suivante dans l’interface de ligne de commande/le terminal :\
`df -ih`

UIse% > 90% ?

a. OUI - Cela est dû à un trop grand nombre de fichiers. Passez en revue les étapes de suppression des fichiers en toute sécurité dans [Suppression de fichiers en toute sécurité en cas de manque d’espace disque, Adobe Commerce sur l’infrastructure cloud](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). Passez à l’ [étape 2](#step-2) une fois ces étapes terminées. Si vous souhaitez demander plus d&#39;espace, [soumettez un ticket d&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NON - Vérifier l’espace. Exécutez `df -h | grep mysql`, puis `df -h | grep tmp` dans l’interface de ligne de commande/le terminal pour vérifier l’utilisation de l’espace disque dans les répertoires `/tmp` et `/data/mysql`. Passez à [Étape 3](#step-3).

+++

## Etape 2 - Vérifier l&#39;espace disque {#step-2}

+++**Vérifiez l’utilisation de l’espace disque ?**

Une fois que vous avez réduit le nombre de fichiers, exécutez `df -h | grep mysql` puis `df -h | grep tmp` dans l’interface en ligne de commande/le terminal pour vérifier l’utilisation de l’espace disque dans `/tmp` et `/data/mysql`. Est-il supérieur à 70 % utilisé pour `/tmp` ou `/data/mysql` ?

a. OUI - Passez à l’ [étape 3](#step-3).
b. NO - Les requêtes peuvent épuiser le stockage disponible. Cela peut entraîner un blocage du noeud, mettant fin à la requête et supprimant les fichiers `tmp`. Examinez la sortie de `SHOW PROCESSLIST;` dans l’interface de ligne de commande [!DNL MySQL] pour rechercher les requêtes qui peuvent être la cause du problème. [Envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), demandant plus d’espace.

+++

## Étape 3 - Identifier le répertoire avec une utilisation élevée {#step-3}

+++**Quel répertoire utilise plus de 70 % ?**

Quel répertoire utilise plus de 70 % ? `/tmp` ou `/data/mysql` ?

>[!NOTE]
>
>Par défaut, tmpdir de base de données écrit sur `/tmp`. Pour vérifier que la configuration de votre base de données est toujours définie sur cette valeur par défaut, exécutez la commande suivante dans l’interface de ligne de commande [!DNL MySQL] : `SHOW VARIABLES LIKE "TMPDIR";` Si le tmpdir de base de données est toujours en train d’écrire sur `/tmp`, `/tmp` apparaîtra dans la colonne Valeur.

a. `/tmp` - Passez à l’ [étape 4](#step-4). \
b. `/data/mysql` - Passez à l’ [étape 5](#step-5).

+++

## Étape 4 - Dépannage du montage /tmp complet {#step-4}

+++**Résolution des problèmes /tmp mont full**

[Résolution des problèmes /tmp de montage complet pour Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), faites défiler l’article vers le bas et essayez les solutions et les bonnes pratiques. Exécutez ensuite `df -h | grep mysql`, puis `df -h | grep tmp` dans l’interface de ligne de commande/le terminal pour vérifier l’utilisation de l’espace disque dans les répertoires `/tmp` et `/data/mysql`\
  &lt; 70 % utilisé ?

>[!NOTE]
>
>Les solutions de [Dépannage /tmp de montage complet pour Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) sont conçues pour les marchands qui n’ont pas modifié les variables de la base de données tmpdir, qui écrit par défaut sur `/tmp`. Si vous avez modifié la valeur de tmpdir, les instructions de [Dépannage /tmp de montage complet pour Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) ne seront pas utiles.

a. OUI - Vous avez résolu le problème. \
b. NO - [Envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), demandant plus d’espace.

+++

## Étape 5 - Vérifier la valeur par défaut {#step-5}

+++**Vérifiez la valeur par défaut**

Il se peut que la configuration de votre base de données ne soit plus celle par défaut d’origine. Recherchez la configuration tmpdir de base de données en exécutant dans l’interface de ligne de commande [!DNL MySQL] : `SELECT @@DATADIR;`. Si `/data/mysql/` est généré, le tmpdir de la base de données écrit maintenant sur `/data/mysql/`. Essayez d’augmenter l’espace dans ce répertoire en suivant les étapes de [[!DNL MySQL] l’espace disque est faible sur Adobe Commerce sur notre infrastructure cloud](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). Exécutez ensuite `df -h | grep mysql`, puis `df -h | grep tmp` dans l’interface de ligne de commande/le terminal pour vérifier l’utilisation de l’espace disque dans `/data/mysql` et `/tmp`.\
  &lt; 70 % utilisé ?

a. OUI - Vous avez résolu le problème. \
b. NO - [Envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), demandant plus d’espace.

+++

[Retour à l’étape 1](#step-1)

## Lecture connexe

* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
