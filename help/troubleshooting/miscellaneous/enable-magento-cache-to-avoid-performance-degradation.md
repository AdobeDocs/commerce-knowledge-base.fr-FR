---
title: Activez le cache pour éviter une dégradation des performances
description: Cet article explique comment résoudre un problème de site lent causé par la désactivation de certains types de cache d’Adobe Commerce.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Activez le cache pour éviter une dégradation des performances

Cet article explique comment résoudre un problème de site lent causé par la désactivation de certains types de cache d’Adobe Commerce.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

## Problème

Vous constatez une dégradation des performances. Par exemple, la page Passage en caisse se charge lentement ou la valeur Apdex diminue dans New Relic.

## Cause

Certaines désactivations de certains types de cache d’Adobe Commerce peuvent entraîner une dégradation des performances.

## Solution

1. Tout d’abord, vérifiez le statut de votre cache Adobe Commerce pour voir si c’est bien le problème. Pour cela, [SSH dans votre environnement](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) et exécutez la commande suivante :

   ```bash
   php bin/magento cache:status
   ```

   Cela affiche le statut de chaque type de cache (« 0 » pour désactivé, « 1 » pour activé). Vous pouvez également obtenir ces informations dans le fichier `app/etc/env.php`.

1. Examinez les types de cache désactivés. Tous les types de cache d’Adobe Commerce doivent être activés, sauf si vous avez reçu d’autres conseils d’Adobe. Les extensions tierces ne doivent pas nécessiter la désactivation du cache d’Adobe Commerce.
1. Si l’enquête confirme que certains types de cache sont désactivés par erreur, activez-les en exécutant la commande suivante pour chaque type de cache : `php bin/magento cache:enable <your_disabled_cache_type>`

En cas d’inquiétude et/ou de question sur la possibilité ou la nécessité de désactiver un certain type de cache Adobe Commerce, [contactez l’assistance Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour obtenir des recommandations.

## Lecture connexe

Documentation sur le cache d’Adobe Commerce dans notre documentation destinée aux développeurs :

* [Présentation du cache Adobe Commerce](https://developer.adobe.com/commerce/frontend-core/guide/caching/)
* [ Gérer le cache ](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/manage-cache)

Autres raisons possibles des problèmes de performances et solutions correspondantes :

* [Désactivez la sortie Adobe Commerce Banner pour améliorer les performances du site.](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)
* [Les tables MySQL sont trop grandes](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26945)
* [Performances lentes, crons lents et à exécution longue](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)
* [Accès administrateur limité provoquant des problèmes de performances](/help/troubleshooting/miscellaneous/restricted-admin-access-causing-performance-issues.md)
