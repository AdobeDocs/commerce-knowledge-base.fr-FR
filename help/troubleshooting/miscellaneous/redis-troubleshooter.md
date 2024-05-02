---
title: Réinitialiser le dépannage sur Adobe Commerce
description: Cet article est un outil de dépannage pour Adobe Commerce sur site et Adobe Commerce sur les marchands d’infrastructure cloud qui rencontrent des problèmes avec Redis. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’outil de dépannage. Selon vos symptômes et votre configuration, l’outil de dépannage explique comment résoudre les problèmes de version et de mémoire et optimiser les performances.
exl-id: 241abcfd-33b8-449b-b385-32950bd26320
feature: Services, Support
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Réinitialiser le dépannage sur Adobe Commerce

Cet article est un outil de dépannage pour Adobe Commerce sur site et Adobe Commerce sur les marchands d’infrastructure cloud qui rencontrent des problèmes avec Redis. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’outil de dépannage. En fonction de vos symptômes, l’outil de dépannage explique comment résoudre les problèmes de version et de mémoire et optimiser les performances.

## Étape 1 - Problème Redis {#step-1}

+++Problème lié à Redis ?

a. OUI - Passez à [Étape 2](#step2)</a>.

b. NO - Revenir à [support.magento.com](https://support.magento.com/hc/en-us) et recherchez les articles de dépannage pertinents.

+++

## Étape 2 - Confirmation des correctifs Redis installés {#step-2}

+++Correctifs Redis actuels installés ?

a. OUI - Passez à [Étape 3](#step3)</a>.

b. NO - Assurez-vous que vous disposez de la dernière version du package. `magento-cloud-patches` installé. Ce paquet contient les correctifs nécessaires pour Redis. Pour accéder à [GitHub Magneto-cloud-Correctifs](https://github.com/magento/magento-cloud-patches/).

+++

## Étape 3 - Confirmation de la prise en charge de la version Redis {#step-3}

+++Sur Redis versions 3.2 ou 5.0 ?

Vérifiez en exécutant les commandes suivantes dans l’interface de ligne de commande. Pro or Staging : `$ redis-cli -p %port-number% info | grep redis_version`, où `%port-number%` est le numéro du port, qui se trouve dans la variable `app/etc/env.php` ou en exécutant l’une des commandes suivantes : `$ vendor/bin/ece-tools env:config:show | grep -i redis -A 3` ou `$ cat app/etc/env.php | grep redis -A 3` Démarrage ou intégration : `$ redis-cli -h 'redis.internal' info | grep redis_version`

a. OUI - Passez à [Étape 4](#step4).

b. NO - Adobe Commerce prend en charge les versions 3.2 et 5.0 de Redis. Si vous exécutez Adobe Commerce sur l’infrastructure cloud 2.3.3 ou version ultérieure, nous vous recommandons d’effectuer une mise à niveau vers Redis 5. Pour connaître les étapes de configuration d’Adobe Commerce sur l’infrastructure cloud Architecture de plan Pro, les environnements d’intégration et de démarrage, y compris la branche principale, reportez-vous à la section [Adobe Commerce sur l’infrastructure cloud > Configuration du service Redis](https://devdocs.magento.com/cloud/project/services-redis.html)</a> dans notre documentation destinée aux développeurs. **Vous devez [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour modifier la configuration du service dans les environnements de production et d’évaluation de l’architecture Pro. En outre, pour Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.5+, une mise en oeuvre étendue du cache Redis est recommandée. Ce type d’implémentation du cache Redis fournit des améliorations qui réduisent le nombre de requêtes envoyées aux Redis qui sont effectuées sur chaque requête Adobe Commerce. Pour connaître les étapes, voir [Mise en oeuvre étendue du cache Redis dans Adobe Commerce 2.3.5+](https://support.magento.com/hc/en-us/articles/360049292532) dans notre base de connaissances de soutien. Pour tous les autres utilisateurs Adobe Commerce, reportez-vous à la section [Guide de configuration d’Adobe Commerce > Configurer des redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/config-redis.html) dans notre documentation destinée aux développeurs, pour obtenir des instructions.

+++

## Étape 4 - Vérifier la dernière version des outils de la CEE {#step-4}

+++Avez-vous la dernière version de [Outils de la CEE > v2002.1.1](https://github.com/magento/ece-tools/releases)?

Vérifiez quelle version vous disposez en exécutant la commande dans l’interface de ligne de commande/le terminal : `$php vendor/bin/composer info magento/ece-tools`.

a. OUI - Passez à [Étape 5](#step5).

b. NON - [Mise à niveau des outils CEE](https://devdocs.magento.com/cloud/project/ece-tools-update.html) à la dernière version.

+++

## Étape 5 - Évaluation du trafic réseau {#step-5}

+++Y a-t-il beaucoup de trafic réseau entre l’application et Redis ?

a. OUI - Essayez les éléments suivants : pour une architecture non fractionnée, assurez-vous qu’un [connexion secondaire](/help/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.md) est utilisée. Pour une architecture fractionnée, la variable [Le cache L2 doit être activé.](https://devdocs.magento.com/guides/v2.4/config-guide/cache/two-level-cache.html).

b. NO - Configuration de la configuration du cache L2 par [Mise à jour du serveur principal Redis](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend). Passez à [Étape 6](#step6).

+++

## Étape 6 - Vérification de la vitesse du site {#step-6}

+++Le site fonctionne-t-il encore lentement, après avoir activé le cache L2 ?

a. OUI - Vérification du répertoire temporaire `/dev/shm` pour voir si vous devez augmenter l’espace. Si vous avez besoin d’espace, [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
b. NO - L’activation du cache L2 semble avoir résolu vos problèmes Redis.

+++

[Retour à l’étape 1](#step-1)
