---
title: Mauvaises performances dans les environnements d’intégration
description: Cet article fournit une solution pour le problème de faibles performances des environnements d’intégration Pro et d’évaluation de Starter.
feature: Integration, Staging
role: Developer
source-git-commit: c0e2a8fdd2e4d231e56a3121544dbd8a25a8d60c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Mauvaises performances dans les environnements d’intégration

Cet article fournit une solution pour le problème de faibles performances des environnements d’intégration Pro et d’évaluation de Starter.

## Produits et versions concernés :

* Adobe Commerce sur l’infrastructure cloud (toutes versions)

## Problème

Votre environnement d’intégration Pro ou votre environnement d’évaluation Starter ne fonctionnent pas correctement.

## Cause

Selon la taille de votre catalogue/données ou les exigences de vos intégrations/personnalisations tierces, les ressources disponibles dans les environnements d’intégration peuvent avoir dépassé.

## Solution

Pour résoudre les problèmes de performances, veillez à suivre les bonnes pratiques relatives aux meilleures performances dans l’environnement d’intégration. Vous devrez peut-être également demander une mise à niveau des environnements pour améliorer l’intégration.

Tout d’abord, déterminez si votre environnement se trouve sur la [configuration d’intégration améliorée](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter).

* [Pro Architecture](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Architecture de démarrage](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Consultez le journal de déploiement à l’aide de l’une de ces méthodes.

### Méthode 1 :

Exécutez la commande suivante à l’aide de l’interface de ligne de commande de Cloud :

`magento-cloud activity:log -e <branch name>`

### Méthode 2 :

Vérifiez le journal de déploiement le plus récent pour cet environnement dans la [console cloud](https://console.adobecommerce.com).

À la fin du journal de déploiement, si vous voyez quelque chose comme ceci (la première ligne affiche la taille=XL et les lignes restantes la taille=L), cela signifie que vous êtes sur la configuration de l’intégration améliorée.

```
Environment configuration
mymagento (type: php:8.2, size: XL, disk: 5120)
mysql (type: mysql:10.6, size: L, disk: 5120)
redis (type: redis:7.2, size: L)
opensearch (type: opensearch:2, size: L, disk: 1024)
rabbitmq (type: rabbitmq:3.12, size: L, disk: 1024)
```

Si vous n’utilisez pas la configuration d’intégration améliorée, vous pouvez [ demander l’amélioration/la mise à niveau](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter).
Si vous utilisez déjà la configuration de l’intégration améliorée ou que vous rencontrez toujours des problèmes de performances après la mise à niveau, veillez à suivre les bonnes pratiques pour des performances optimales dans l’environnement d’intégration :

* [Pro Architecture](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Architecture de démarrage](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Si vous avez satisfait aux recommandations ci-dessus, [soumettez une demande d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) pour obtenir une assistance supplémentaire.
 
