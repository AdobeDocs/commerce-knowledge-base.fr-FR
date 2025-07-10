---
title: Résolution des problèmes de déploiement d’Adobe Commerce
description: Les déploiements bloqués et les déploiements ayant échoué sur Adobe Commerce peuvent être résolus à l’aide de l’outil de dépannage de déploiement. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’utilitaire de dépannage.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: d2c37f4465d5ba4f4b4878eae292fa805d1dc45b
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Résolution des problèmes de déploiement d’Adobe Commerce

Les déploiements bloqués et les déploiements ayant échoué sur Adobe Commerce peuvent être résolus à l’aide de l’outil de dépannage de déploiement. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’utilitaire de dépannage.

## Étape 1 : vérifier que le service est en cours d’exécution {#step-1}

+++**Adobe Commerce sur le service d’infrastructure cloud est-il opérationnel ?**

Déploiement bloqué - Le service d’infrastructure cloud d’Adobe Commerce est-il opérationnel ? Cochez [Adobe Commerce Cloud](https://status.adobe.com/products/3350/).

a. OUI - Passer à [étape 2](#step-2).\
b. NON - Maintenance ou pannes globales. Recherchez une estimation de la durée et des mises à jour.

+++

## Étape 2 - Vérifier les déploiements dans d’autres environnements {#step-2}

+++**Existe-t-il des déploiements dans d’autres environnements qui bloquent le déploiement dans l’environnement existant ?**

Pour obtenir la liste des activités en cours, exécutez la commande suivante à l’aide de l’interface de ligne de commande magento-cloud (si vous n’avez été ajouté qu’à un seul projet cloud). **Remarque** : vérifiez que vous disposez de la dernière version de l’interface de ligne de commande magento-cloud. Pour connaître les étapes, reportez-vous à la section [Mise à jour de l’interface de ligne de commande](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/dev-tools/cloud-cli/cloud-cli-overview) du guide Commerce sur les infrastructures cloud.

```bash
magento-cloud --state=in_progress
```

Pour obtenir une liste des activités en cours, exécutez la commande suivante à l’aide de l’interface de ligne de commande magento-cloud (si vous avez été ajouté à plusieurs projets) :

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

Pour obtenir des informations sur une activité de déploiement existante (voir la section [Vérification du journal de déploiement si l’interface utilisateur de Cloud comporte une erreur « journal arrêté »](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
pour plus d’informations), vous pouvez exécuter cette commande pour obtenir un journal d’exécution de cette activité :

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. OUI - Résolution des problèmes de l’autre environnement qui bloque le déploiement dans l’environnement existant. Passez à [étape 3](#step-3).

b. NON - Résolution des problèmes liés à l’environnement actuel. Passez à [étape 3](#step-3).

+++


## Étape 3 : vérification de SSH sur tous les nœuds {#step-3}

+++**SSH réussi sur tous les nœuds ?**

a. OUI - Passer à [étape 4](#step-4).\
b. NON - [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Étape 4 : vérifier tous les services en cours d’exécution {#step-4}

+++**Tous les services en cours d’exécution ?**

a. OUI - Passer à [étape 5](#step-5).\
b. NON - [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Étape 5 - Vérification de l’exécution du Bitbucket {#step-5}

+++**Utilisation de Bitbucket ?**

a. OUI - Vérifiez [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NON - Vérifiez les erreurs du journal de déploiement dans les journaux [Créer et déployer](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/test/log-locations). Passez à [étape 6](#step-6).

+++

## Étape 6 - Vérification des codes d’erreur {#step-6}

+++**Code d’erreur signalé ?**

a. OUI - Passer à [étape 7](#step-7).\
b. NON - Passer à [étape 8](#step-8).

+++

## Etape 7 - 403 Erreur Interdite {#step-7}

+++**403 Interdit ?**

a. OUI - Passer à [étape 16](#step-16).
b. NON - Passer à [étape 9](#step-9).

+++

## Étape 8 : vérification des tâches cron en cours d’exécution {#step-8}

+++**Les tâches cron sont-elles en cours d’exécution ?** Connectez-vous par ssh sur la branche et exécutez `ps aufxx |grep cron`.

a. OUI - Connectez-vous par ssh sur la branche affectée (par exemple, principale). Tuer et déverrouiller les emplois cron. Cette action entraîne la suppression des tâches cron et la réinitialisation du statut. Exécutez `php vendor/bin/ece-tools cron:kill` puis `php vendor/bin/ece-tools cron:unlock`. Si vous étiez en train de fusionner un environnement dans un autre, vérifiez que les deux environnements exécutent crons.\
b. NON - Passer à [étape 17](#step-17).

+++

## Etape 9 - Erreur application déployable sur le cluster distant {#step-9}

+++**Erreur Impossible de charger l’application dans le cluster distant ?**

a. OUI - Passer à [étape 10](#step-10).\
b. NON - Passer à [étape 11](#step-11).

+++

## Étape 10 - Vérifier que le stockage est suffisant {#step-10}

+++**Stockage disponible correct ?**

* [Vérifier l’environnement d’intégration/de démarrage](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space?lang=en#check-integration-environment)
* [Rechercher un environnement d’évaluation/de production Pro](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space?lang=en#check-dedicated-clusters)

a. OUI - Procédez à l’[étape 11](#step-11).\
b. NON - Vérifiez [Gérer l’espace disque](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space).

+++

## Étape 11 - Vérification de l’espace disque {#step-11}

+++**_fichier n&#39;a pas pu être écrit Avertissement _?**

a. OUI

* Pour les environnements d’intégration/de démarrage :

   * Veuillez [augmenter la valeur du disque en .magento.app.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=fr#application-disk-space) et redéployer. Si cela ne fonctionne pas, [envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
   * Vous pouvez également passer en revue le dossier `var/log` et supprimer tous les fichiers journaux de plus de 1 Mo. Exécutez cette commande pour vérifier les tailles de fichier :

     ```bash
     ls -la var/log
     ```

* Pour les environnements d’évaluation/de production Pro :

   1. Envoyez un ticket d’assistance pour ajouter du stockage.

b. NON - Procédez à [étape 12](#step-12).

+++

## Étape 12 - Échec du redéploiement de l’environnement {#step-12}

+++**Erreur d’échec du redéploiement de l’environnement ?**

a. OUI - Procédez à l’[étape 13](#step-13).\
b. NON - Procédez à [étape 8](#step-8).

+++

## Étape 13 - Vérification de l’échec de la mise à niveau d’Elasticsearch {#step-13}

+++**Elasticsearch en cours de mise à niveau ou de déploiement ?**

a. OUI - Les étapes de mise à niveau d’Elasticsearch ont échoué. Pour plus d&#39;informations, consultez la section [Compatibilité logicielle Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Si la mise à niveau d’Elasticsearch ne fonctionne toujours pas, [envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Remarque** : sur Adobe Commerce sur les infrastructures cloud, sachez que les mises à niveau de service ne peuvent pas être envoyées à l’environnement de production sans avis de 48 heures ouvrables à notre équipe en charge de l’infrastructure. Cela est nécessaire car nous devons nous assurer qu’un ingénieur du support à l’infrastructure est disponible pour mettre à jour votre configuration dans le délai souhaité avec un temps d’arrêt minimal pour votre environnement de production. Ainsi, 48 heures avant le moment où vos modifications doivent être mises en production, [soumettez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) détaillant la mise à niveau de service requise et indiquant l’heure à laquelle vous souhaitez que le processus de mise à niveau démarre.\
b. NON - Passer à [étape 14](#step-14).

+++

## Étape 14 - Vérifier les limites d&#39;espace {#step-14}

+++**Le système de fichiers manque d’inodes ou d’espace ?**

a. OUI - Voir [Gérer l’espace disque](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=fr#application-disk-space).\
b. NON - Passer à [étape 15](#step-15).

+++

## Étape 15 - Erreur de version Elasticsearch {#step-15}

+++**Erreur sur les versions d’Elasticseach ?**

a. OUI - Passer à [étape 16](#step-16).\
b. NON - Passer à [étape 21](#step-21).

+++

## Étape 16 - Vérification de la configuration du compositeur {#step-16}

+++**La configuration du compositeur est-elle correcte ?**

a. OUI - Passer à [étape 10](#step-10).\
b. NON - Consultez [page web du dépanneur du compositeur](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Étape 17 - Rechercher les processus à long terme {#step-17}

+++**Processus à long terme ?**

a. OUI - Identifier les processus à long terme, puis supprimer les processus :
1. Exécutez la commande suivante dans le terminal : `ps aufx`.
1. Recherchez le PID du processus en cours d’exécution.
1. Terminez le processus à l’aide de `kill -9 <PID>`.

Surveillez les déploiements pour la récurrence.

b. NON - Passer à [étape 18](#step-18).

+++

## Étape 18 - Vérifier la défaillance du crochet de poteau {#step-18}

+++**Échec/blocage du crochet de publication ?**

a. OUI - Base de données : [Espace disque disponible](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=fr#allocate-disk-space), corruption, tables incomplètes/corrompues.\
b. NON - Passer à [étape 19](#step-19).

+++

## Étape 19 - Vérifier si les extensions tierces bloquent le déploiement {#step-19}

+++**Utilisation d’extensions tierces ?**

a. OUI - Essayez de [désactiver les extensions tierces](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure-store/extensions) et d’exécuter le déploiement (pour voir si elles sont à l’origine du problème), en particulier si des noms d’extension figurent dans des erreurs.\
b. NON - Passer à [étape 20](#step-20).

+++

## Étape 20 - Rechercher les requêtes lentes {#step-20}

+++**Requêtes de longue durée ?**

[Vérifiez le journal des requêtes lentes et MySQL show processlist](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. OUI - Interrompt toutes les requêtes longues. Vérifiez [Syntaxe de MySQL Kill.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b. NON - [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Étape 21 - Rétrogradation de la version d’Elasticsearch {#step-21}

+++**Mise à niveau des versions d’Elasticsearch ?**

a. OUI - Impossible d’effectuer la configuration. [Envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NON - [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Retour à l’étape 1](#step-1)
