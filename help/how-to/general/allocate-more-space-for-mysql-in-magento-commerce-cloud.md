---
title: Allouer plus d’espace pour MySQL dans Adobe Commerce sur le cloud
description: Cet article explique comment allouer plus d’espace à MySQL dans Adobe Commerce sur les infrastructures cloud.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Allouer plus d’espace pour MySQL dans Adobe Commerce sur le cloud


## Allouer de l’espace sur l’intégration du plan de démarrage et du plan pro

Pour tous les environnements de plan de démarrage et de plan Pro [environnement d’intégration](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242), vous pouvez allouer plus d’espace à MySQL dans le fichier `.magento/services.yaml` en augmentant le paramètre `mysql: disk:`. Par exemple :

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Consultez l’article [Configurer le service MySQL](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql) pour plus de références.

Une fois que vous avez modifié le fichier `.magento/services.yaml`, vous devez valider et transmettre vos modifications pour qu’elles soient appliquées. La notification push déclenche le processus de déploiement.

>[!WARNING]
>
>Une partition de plan de démarrage ne doit jamais être réduite (par exemple, passer de 30 Go à 20 Go), car cela entraînera probablement une corruption catastrophique des données.

## Allouer de l&#39;espace sur l&#39;évaluation ou la production Pro Plan

Pour apporter ces modifications à l&#39;environnement d&#39;évaluation ou de production du plan Pro, vous devez créer un ticket d&#39;assistance [support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). Lors de l’envoi d’un ticket d’assistance pour augmenter le stockage, l’assistance devra connaître la quantité et la répartition auxquelles le stockage doit être appliqué (`/mysql` ou `/exports`). Une demande d’augmentation du stockage nécessite l’approbation de l’équipe de votre compte Adobe, qui examinera la quantité de stockage à laquelle vous avez droit (conformément au formulaire de commande) avant de l’approuver.

## Diminution de l&#39;espace alloué non disponible (plan Pro et Starter)

La prise en charge d’Adobe Commerce peut agrandir une partition (`/mysql` ou `/exports`), mais ne peut pas la réduire. Si vous procédez de la sorte, il y a un risque de corruption des données. C’est pourquoi la diminution du stockage pour une partition n’est pas disponible.
C&#39;est également vrai pour le plan de démarrage, où vous pouvez augmenter l&#39;espace alloué vous-même : diminuer est fortement déconseillé et peut entraîner une corruption catastrophique des données.
