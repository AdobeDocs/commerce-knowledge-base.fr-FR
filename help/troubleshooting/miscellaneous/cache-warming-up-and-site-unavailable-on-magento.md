---
title: Mise en cache et site indisponible sur Adobe Commerce
description: Cet article fournit une solution lorsque le cache de la page se réchauffe et qu’il y a un déploiement bloqué ou un site en panne.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Mise en cache et site indisponible sur Adobe Commerce

Cet article fournit une solution lorsque le cache de la page se réchauffe et qu’il y a un déploiement bloqué ou un site en panne.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, tous [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problème

Le script de nettoyage de la mémoire cache, à la fin de la phase de post-déploiement, envoie les demandes à un débit si élevé que certaines instances, comme 4 processeurs, ne peuvent pas gérer. Leur épingle épuise le nombre de travailleurs.

<u>Étapes à reproduire</u>:

Démarrez les opérations de nettoyage du cache.

<u>Résultat attendu</u>:

Pages ou chargement de site entier.

<u>Résultat réel</u>:

Le site n’est pas disponible ou le temps de réponse est trop élevé.

## Solution

Limitez le nombre de connexions simultanées pendant le nettoyage du cache. Cela nécessite l’ajout de la variable `WARM_UP_CONCURRENCY` post-déploiement pour spécifier le nombre de demandes de nettoyage que le script de nettoyage du cache peut envoyer simultanément. La définition de cette option peut vous aider à gérer la charge sur l’infrastructure cloud Adobe Commerce. Pour connaître les étapes, voir [Variables de post-déploiement > WARM\_UP\_CONCURRENCY](https://devdocs.magento.com/cloud/env/variables-post-deploy.html#warm_up_concurrency) dans notre documentation destinée aux développeurs.

## Lecture connexe

[Cache de page entière](https://docs.magento.com/user-guide/system/cache-full-page.html) dans notre guide d’utilisation
