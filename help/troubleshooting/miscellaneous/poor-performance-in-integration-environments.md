---
title: Mauvaises performances dans les environnements d’intégration
description: Cet article fournit une solution au problème de mauvaises performances des environnements d’intégration Pro et des environnements d’évaluation Starter.
feature: Integration, Staging
role: Developer
exl-id: 46110dbc-2f54-4654-95e2-39e8ae1e6979
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Mauvaises performances dans les environnements d’intégration

Cet article fournit une solution au problème de mauvaises performances des environnements d’intégration Pro et des environnements d’évaluation Starter.

## Produits et versions concernés :

* Adobe Commerce sur les infrastructures cloud (toutes versions)

## Problème

Votre environnement d’intégration Pro ou votre environnement d’évaluation Starter ne fonctionne pas correctement.

## Cause

Selon la taille de votre catalogue/données ou les exigences de vos intégrations/personnalisations tierces, les ressources disponibles dans les environnements d’intégration peuvent avoir dépassé.

## Solution

Pour résoudre les problèmes de performances, veillez à suivre les bonnes pratiques en matière de performances dans l’environnement d’intégration. Vous devrez peut-être également demander une mise à niveau des environnements pour améliorer l’intégration.

Tout d’abord, déterminez si votre environnement se trouve dans la [configuration d’intégration améliorée](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242).

* [Architecture Pro](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Architecture de démarrage](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Vérifiez le journal de déploiement à l’aide de l’une de ces méthodes.

### Méthode 1 :

Exécutez la commande suivante à l’aide de l’interface de ligne de commande Cloud :

`magento-cloud activity:log -e <branch name>`

### Méthode 2 :

Vérifiez le journal de déploiement le plus récent pour cet environnement dans la [console cloud](https://console.adobecommerce.com).

À la fin du journal de déploiement, si vous voyez quelque chose comme ceci : la première ligne indique la taille=XL, et les lignes restantes indiquent la taille=L, cela signifie que vous êtes sur la configuration d’intégration améliorée.

```
Environment configuration
mymagento (type: php:8.2, size: XL, disk: 5120)
mysql (type: mysql:10.6, size: L, disk: 5120)
redis (type: redis:7.2, size: L)
opensearch (type: opensearch:2, size: L, disk: 1024)
rabbitmq (type: rabbitmq:3.12, size: L, disk: 1024)
```

Si vous ne disposez pas de la configuration d’intégration améliorée, vous pouvez [demander l’amélioration/la mise à niveau](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242).
Si vous utilisez déjà la configuration d’intégration améliorée ou que vous rencontrez toujours des problèmes de performances après la mise à niveau, veillez à suivre les bonnes pratiques pour obtenir des performances optimales dans l’environnement d’intégration :

* [Architecture Pro](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Architecture de démarrage](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Si vous avez répondu aux recommandations ci-dessus, [envoyez une demande d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) pour obtenir une assistance supplémentaire.
