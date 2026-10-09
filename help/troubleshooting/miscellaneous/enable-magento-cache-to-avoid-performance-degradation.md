---
title: Activez le cache pour éviter une dégradation des performances
description: Cet article explique comment résoudre un problème de site lent causé par la désactivation de certains types de cache d’Adobe Commerce.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '366'
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

En cas d’inquiétude et/ou de question sur la possibilité ou la nécessité de désactiver un certain type de cache Adobe Commerce, [contactez l’assistance Adobe Commerce](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) pour obtenir des recommandations.

## Lecture connexe

Documentation sur le cache d’Adobe Commerce dans notre documentation destinée aux développeurs :

* [Présentation du cache d’Adobe Commerce](https://developer.adobe.com/commerce/frontend-core/guide/caching)
* [Gérer le cache](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/manage-cache)

Autres raisons possibles des problèmes de performances et solutions correspondantes :

* [Désactivez la sortie Adobe Commerce Banner pour améliorer les performances du site.](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26909)
* [Tables MySQL trop volumineuses](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26945)
* [Performances lentes, crons lents et à exécution longue](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-42802)
