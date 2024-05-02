---
title: Le service Redis est bloqué.
description: L’article recommande comment corriger Redis.
exl-id: 5eb8fb70-0f41-433a-8d3f-c368781a2d1d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Le service Redis est bloqué.

L’article recommande comment corriger Redis.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x., 2.3x
* Toutes les versions de Redis

## Problème

Lenteur ou panne du site web en raison d’un débordement de mémoire dans Redis.

## Cause

Un débordement de mémoire peut entraîner le blocage du service Redis. Pendant le pic, le service Redis peut nécessiter plus de mémoire que ce qui est actuellement alloué.

## Solution

Pour vérifier la configuration actuelle et la mémoire utilisée, exécutez la commande suivante dans l’interface de ligne de commande. Il recherche la mémoire utilisée, le maximum de mémoire, les clés expulsées et le temps de réapprovisionnement en jours :

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

La variable *REDIS\_PORT* et *REDIS\_HOST* peuvent être récupérées à partir de `app/etc/env.php`.

Si la sortie de l’exécution de la requête ci-dessus indique que le pourcentage de mémoire libre est inférieur à 40 %, [envoyer un ticket à l’assistance Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demandant une augmentation de la variable `maxmemory` dans Redis Server. Si la valeur des clés expulsées n’est pas &quot;0&quot; ou que la durée de réactivation en jours est égale à 0 (ce qui indique que Redis s’est bloqué aujourd’hui), vous devez également [envoyer un ticket à l’assistance Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demande d’une enquête et d’un correctif pour ce problème.

## Lecture connexe

Pour en savoir plus sur la mémoire Redis, reportez-vous à [Optimisation de la mémoire Redis](https://redis.io/topics/memory-optimization).
