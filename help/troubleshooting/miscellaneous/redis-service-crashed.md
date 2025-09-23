---
title: Service Redis bloqué
description: L'article recommande comment réparer Redis.
exl-id: 5eb8fb70-0f41-433a-8d3f-c368781a2d1d
feature: Services
role: Developer
source-git-commit: 649e01b29b59bf77e6396acbeb7a83bd9c67e1ef
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Service Redis bloqué

L&#39;article recommande comment réparer Redis.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud 2.2.x. et 2.3.x
* Adobe Commerce on-premise 2.2.x., 2.3x
* Toutes les versions de Redis

## Problème

Lenteur ou panne du site Web due à un dépassement de mémoire à Redis.

## Cause

Un dépassement de mémoire peut entraîner le blocage du service Redis. Pendant les heures de pointe, le service Redis peut nécessiter plus de mémoire que celle actuellement allouée.

## Solution

Pour vérifier la configuration actuelle et la mémoire utilisée, exécutez la commande suivante dans l’interface de ligne de commande. Il vérifie la mémoire utilisée, maxmemory, les clés évincées et le temps de reprise en jours :

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

Les variables *REDIS\_PORT* et *REDIS\_HOST* peuvent être récupérées à partir de `app/etc/env.php`.

>[!NOTE]
>
>Vous pouvez également récupérer l’adresse et le numéro de port de l’hôte Redis en exécutant cette commande d’interface de ligne de commande :
>   
```bash
>   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
>   ```


Si la sortie de l’exécution de la requête ci-dessus indique que le pourcentage de mémoire libre est inférieur à 40 %, [envoyez un ticket à l’assistance Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) en demandant une augmentation du paramètre `maxmemory` dans Redis Server. Si la valeur des clés évincées n’est pas « 0 » ou si le temps d’attente de Redis en jours est égal à 0 (indiquant que Redis s’est bloqué aujourd’hui), vous devez également [envoyer un ticket à l’assistance d’Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) afin de demander une enquête et un correctif pour ce problème.

## Lectures connexes

Pour en savoir plus sur la mémoire Redis, consultez [Optimisation de la mémoire Redis](https://redis.io/topics/memory-optimization).
