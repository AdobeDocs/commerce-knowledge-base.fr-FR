---
title: Dépannage du déploiement d’Adobe Commerce
description: Les déploiements bloqués et les déploiements ayant échoué sur Adobe Commerce peuvent être résolus à l’aide de l’outil de dépannage du déploiement . Cliquez sur chaque question pour afficher la réponse à chaque étape de l’outil de dépannage.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: 6177863da268f43cc30119cef6f718a04c46b3e6
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# Dépannage du déploiement d’Adobe Commerce

Les déploiements bloqués et les déploiements ayant échoué sur Adobe Commerce peuvent être résolus à l’aide de l’outil de dépannage du déploiement . Cliquez sur chaque question pour afficher la réponse à chaque étape de l’outil de dépannage.

## Étape 1 - Vérification de l’exécution du service {#step-1}

+++**Adobe Commerce est-il mis en service pour l’infrastructure cloud ?**

Stuck Deployment - Adobe Commerce est-il en service d’infrastructure cloud ? Vérifier [Adobe Commerce Cloud](https://status.adobe.com/products/3350/).

a. OUI - Passez à [Étape 2](#step-2).\
b. NO - Maintenance ou pannes globales. Recherchez la durée estimée et les mises à jour.

+++

## Étape 2 - Vérifier les déploiements dans d’autres environnements {#step-2}

+++**Existe-t-il des déploiements dans d’autres environnements qui bloquent le déploiement dans l’environnement existant ?**

Pour obtenir une liste des activités en cours, exécutez la commande suivante à l’aide de l’interface de ligne de commande magento-cloud (si vous n’avez été ajouté qu’à un seul projet cloud) :

```bash
magento-cloud --state=in_progress
```

Pour obtenir une liste des activités en cours, exécutez la commande suivante à l’aide de l’interface de ligne de commande magento-cloud (si vous avez été ajouté à plusieurs projets) :

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

Pour obtenir des informations sur une activité de déploiement existante (voir [Vérification du journal de déploiement si l’interface utilisateur de Cloud a &quot;extrait de journal&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
pour plus d’informations) vous pouvez exécuter cette commande pour obtenir un journal d’exécution de cette activité :

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. OUI - Résolution des problèmes liés à l’autre environnement bloquant le déploiement dans l’environnement existant. Passez à [Étape 3](#step-3).

b. NO - Résolution des problèmes liés à l’environnement actuel. Passez à [Étape 3](#step-3).

+++


## Étape 3 - Vérification du SSH sur tous les noeuds {#step-3}

+++**SSH réussi sur tous les noeuds ?**

a. OUI - Passez à [Étape 4](#step-4).\
b. NON - [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Étape 4 - Vérifier tous les services en cours d’exécution {#step-4}

+++**Tous les services en cours d’exécution ?**

a. OUI - Passez à [Étape 5](#step-5).\
b. NON - [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Étape 5 - Vérification de l’exécution du compartiment {#step-5}

+++**Utilisation de Bitbucket ?**

a. OUI - Vérifier [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NO - Vérifier les erreurs du journal de déploiement dans la variable [Création et déploiement des journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html). Passez à [Étape 6](#step-6).

+++

## Étape 6 - Vérifier les codes d’erreur {#step-6}

+++**Code d’erreur signalé ?**

a. OUI - Passez à [Étape 7](#step-7).\
b. NO - Passez à [Étape 8](#step-8).

+++

## Etape 7 - 403 Erreur interdite {#step-7}

+++**403 Interdit ?**

a. OUI - Passez à [Étape 16](#step-16).
b. NO - Passez à [Étape 9](#step-9).

+++

## Étape 8 - Vérification des tâches cron en cours d’exécution {#step-8}

+++**Les tâches cron sont-elles en cours d’exécution ?** Connectez-vous par ssh sur la branche et exécutez `ps aufxx |grep cron`.

a. OUI - Connectez-vous par ssh sur la branche affectée (par exemple, principale). Tuer et déverrouiller les tâches cron. Cela va supprimer les tâches cron et réinitialiser l’état. Exécuter `php vendor/bin/ece-tools cron:kill` puis `php vendor/bin/ece-tools cron:unlock`. Si vous étiez en train de fusionner un environnement dans un autre, vérifiez que les deux environnements exécutent des crons.\
b. NO - Passez à [Étape 17](#step-17).

+++

## Étape 9 - Déploiement de l’application sur une erreur de grappe distante {#step-9}

+++**Impossible de charger l’application vers l’erreur de cluster distant ?**

a. OUI - Passez à [Étape 10](#step-10).\
b. NO - Passez à [Étape 11](#step-11).

+++

## Étape 10 - Vérifier un stockage suffisant {#step-10}

+++**Stockage disponible correct ?**

a. OUI - Procédez à [Étape 11](#step-11).\
b. NON - Révision [Gestion de l’espace disque](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html).

+++

## Étape 11 - Vérification de l’espace disque {#step-11}

+++**_Impossible d’écrire le fichier Avertissement _?**

a. OUI - S&#39;il vous plaît [augmenter la valeur du disque dans .magento.app.yaml ;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space) et redéployez. Si cela ne fonctionne pas, [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NON - Procédez comme suit : [Étape 12](#step-12).

+++

## Étape 12 - Erreur de redéploiement de l’environnement {#step-12}

+++**Erreur du redéploiement de l’environnement ?**

a. OUI - Procédez à [Étape 13](#step-13).\
b. NON - Procédez comme suit : [Étape 8](#step-8).

+++

## Étape 13 - Échec de la vérification de la mise à niveau des Elasticsearch {#step-13}

+++**Elasticsearch mis à niveau ou déployé ?**

a. OUI - Etapes de mise à niveau de l’Elasticsearch ayant échoué. Voir [Compatibilité des logiciels Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Si la mise à niveau Elasticsearch ne fonctionne toujours pas, [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Remarque**: sur Adobe Commerce sur l’infrastructure cloud, sachez que les mises à niveau de service ne peuvent pas être transférées vers l’environnement de production sans préavis de 48 heures ouvrables à notre équipe d’infrastructure. Cela est nécessaire, car nous devons nous assurer qu’un ingénieur du support de l’infrastructure est disponible pour mettre à jour votre configuration dans les délais impartis, avec un temps d’arrêt minimal pour votre environnement de production. 48 heures avant que vos modifications ne soient en production, [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) détaillant la mise à niveau de service requise et indiquant l’heure à laquelle le processus de mise à niveau doit commencer.\
b. NO - Passez à [Étape 14](#step-14).

+++

## Étape 14 - Vérifier les limites d’espace {#step-14}

+++**Système de fichiers hors informations ou espace ?**

a. OUI - Voir [Gestion de l’espace disque](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space).\
b. NO - Passez à [Étape 15](#step-15).

+++

## Étape 15 - Erreur de version Elasticsearch {#step-15}

+++**Erreur à propos des versions d’Elasticseach ?**

a. OUI - Passez à [Étape 16](#step-16).\
b. NO - Passez à [Étape 21](#step-21).

+++

## Étape 16 - Vérification de la configuration du compositeur {#step-16}

+++**Configuration du compositeur correcte ?**

a. OUI - Passez à [Étape 10](#step-10).\
b. NON - Révision [Page web de dépannage du compositeur](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Étape 17 - Vérifier les processus à long terme {#step-17}

+++**Processus de longue durée ?**

a. OUI - Identifiez les processus à long terme, puis supprimez les processus :
1. Exécutez la commande suivante dans le terminal : `ps aufx`.
1. Localisez le PID du processus de longue durée.
1. Arrêtez le processus à l’aide de `kill -9 <PID>`.

Surveillez les déploiements pour la réoccurrence.

b. NO - Passez à [Étape 18](#step-18).

+++

## Étape 18 - Vérification de l’échec du crochet de publication {#step-18}

+++**Échec/blocage du crochet de publication ?**

a. OUI - Base de données : [Espace disque disponible](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#allocate-disk-space), corruption, tables incomplètes/corrompues.\
b. NO - Passez à [Étape 19](#step-19).

+++

## Étape 19 - Vérifier si les extensions tierces bloquent le déploiement {#step-19}

+++**Utilisation d’extensions tierces ?**

a. OUI - Essayez [Désactivation des extensions tierces](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html) et l’exécution du déploiement (pour voir s’ils sont la cause du problème), en particulier si des noms d’extension figurent dans des erreurs.\
b. NO - Passez à [Étape 20](#step-20).

+++

## Étape 20 - Recherche de requêtes lentes {#step-20}

+++**Requêtes longues ?**

[Vérifier le journal des requêtes lentes et la liste des processus d’affichage MySQL](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. OUI - Tuez toutes les requêtes longues. Réviser [Syntaxe de la mort MySQL.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b. NON - [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Étape 21 - Dégrader la version Elasticsearch {#step-21}

+++**Mise à niveau des versions d’Elasticsearch ?**

a. OUI - Ne peut pas être effectué par le biais de la configuration. [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NON - [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Retour à l’étape 1](#step-1)
