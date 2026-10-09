---
title: Préchauffage du cache et site indisponible sur Adobe Commerce
description: Cet article fournit une solution pour le cas où le cache de page se préchauffe et qu’un déploiement ou un site est bloqué.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%
---
# Préchauffage du cache et site indisponible sur Adobe Commerce

Cet article fournit une solution pour le cas où le cache de page se préchauffe et qu’un déploiement ou un site est bloqué.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, toutes les [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problème

Le script de préchauffage du cache, à la fin de la phase post-déploiement, envoie les requêtes à un taux si élevé que certaines instances, comme celles à 4 processeurs, ne peuvent pas faire face. Leur engin épuise le nombre de travailleurs.

<u>Procédure à suivre </u> :

Démarrez les opérations de préchauffage du cache.

<u>Résultat attendu </u> :

Chargements de pages ou de sites entiers.

<u>Résultat réel</u> :

Le site n’est pas disponible ou le temps de réponse est trop long.

## Solution

Limitez le nombre de connexions simultanées pendant la préchauffage du cache. Cela nécessite l’ajout de la variable post-déploiement `WARM_UP_CONCURRENCY` pour spécifier le nombre de requêtes de préchauffage que le script de préchauffage du cache peut envoyer simultanément. La définition de cette option peut vous aider à gérer la charge sur l’infrastructure cloud d’Adobe Commerce. Pour connaître les étapes, consultez [Variables de post-déploiement > WARM\_UP\_CONCURRENCY](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-post-deploy#warm_up_concurrency) dans notre documentation destinée aux développeurs et développeuses.

## Lecture connexe

[Full-Page Cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching) dans notre guide de l’utilisateur
