---
title: Activation du cache pour éviter la dégradation des performances
description: Cet article explique comment résoudre un problème de site lent dû à la désactivation de certains types de cache Adobe Commerce.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

1. Tout d’abord, vérifiez l’état de votre cache Adobe Commerce pour voir s’il s’agit du problème. Pour cela, [SSH vers votre environnement](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) et exécutez la commande suivante :

   ```bash
   php bin/magento cache:status
   ```

   Cela afficherait l’état de chaque type de cache (&quot;0&quot; pour désactivé, &quot;1&quot; pour activé). Vous pouvez également obtenir ces informations dans le fichier `app/etc/env.php`.

1. Examinez les types de cache désactivés. Tous les types de cache Adobe Commerce doivent être activés, sauf si vous avez reçu d’autres conseils d’Adobe de votre part. Les extensions tierces ne doivent pas nécessiter la désactivation du cache Adobe Commerce.
1. Si l&#39;enquête confirme que certains types de cache sont désactivés par erreur, activez-les en exécutant la commande suivante pour chaque type de cache : `php bin/magento cache:enable <your_disabled_cache_type>`

Si vous avez des questions ou des questions concernant la désactivation ou la désactivation d’un certain type de cache Adobe Commerce, [contactez le support Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour demander des recommandations.

## Lecture connexe

Documentation sur le cache Adobe Commerce dans notre documentation destinée aux développeurs :

* [Présentation du cache Adobe Commerce](https://developer.adobe.com/commerce/frontend-core/guide/caching/)
* [Gérer le cache](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-cache)

Autres raisons possibles de problèmes de performances et solutions pour eux :

* [Désactiver la sortie de la bannière Adobe Commerce pour améliorer les performances du site](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)
* [Les tables MySQL sont trop grandes](/help/troubleshooting/database/mysql-tables-are-too-large.md)
* [Lenteur des performances, lenteur et longueur des fils](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)
* [Restriction de l’accès administrateur provoquant des problèmes de performances](/help/troubleshooting/miscellaneous/restricted-admin-access-causing-performance-issues.md)
