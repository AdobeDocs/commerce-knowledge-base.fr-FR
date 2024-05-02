---
title: Activation du cache pour éviter la dégradation des performances
description: Cet article explique comment résoudre un problème de site lent dû à la désactivation de certains types de cache Adobe Commerce.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Activation du cache pour éviter la dégradation des performances

Cet article explique comment résoudre un problème de site lent dû à la désactivation de certains types de cache Adobe Commerce.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

## Problème

Vous constatez une dégradation des performances. Par exemple, la page Passage en caisse se charge lentement ou la valeur Apdex diminue dans New Relic.

## Cause

Certains types de cache Adobe Commerce sont désactivés, ce qui peut entraîner une dégradation des performances.

## Solution

1. Tout d’abord, vérifiez l’état de votre cache Adobe Commerce pour voir s’il s’agit du problème. Pour cela : [SSH vers votre environnement](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) et exécutez la commande suivante :

   ```bash
   php bin/magento cache:status
   ```

   Cela afficherait l’état de chaque type de cache (&quot;0&quot; pour désactivé, &quot;1&quot; pour activé). Ou vous pouvez obtenir ces informations dans le `app/etc/env.php` fichier .

1. Examinez les types de cache désactivés. Tous les types de cache Adobe Commerce doivent être activés, sauf si vous avez reçu d’autres conseils d’Adobe de votre part. Les extensions tierces ne doivent pas nécessiter la désactivation du cache Adobe Commerce.
1. Si l’enquête confirme que certains types de cache sont désactivés par erreur, activez-les en exécutant la commande suivante pour chaque type de cache : `php bin/magento cache:enable <your_disabled_cache_type>`

Si des problèmes et/ou des questions se posent concernant la désactivation ou non d’un certain type de cache Adobe Commerce, [contacter le support Adobe Commerce ;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demande de recommandations.

## Lecture connexe

Documentation sur le cache Adobe Commerce dans notre documentation destinée aux développeurs :

* [Présentation du cache Adobe Commerce](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/cache_for_frontdevs.html)
* [Gestion du cache](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cache.html)

Autres raisons possibles de problèmes de performances et solutions pour eux :

* [Désactiver la sortie de la bannière Adobe Commerce pour améliorer les performances du site](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)
* [Les tables MySQL sont trop grandes](/help/troubleshooting/database/mysql-tables-are-too-large.md)
* [Lenteur des performances, lenteur et longueur des fils](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)
* [Restriction de l’accès administrateur provoquant des problèmes de performances](/help/troubleshooting/miscellaneous/restricted-admin-access-causing-performance-issues.md)
