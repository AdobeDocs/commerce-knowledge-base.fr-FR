---
title: Allouer plus d’espace pour MySQL dans Adobe Commerce sur le cloud
description: Cet article explique comment allouer plus d’espace à MySQL dans Adobe Commerce sur l’infrastructure cloud.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Allouer plus d’espace pour MySQL dans Adobe Commerce sur le cloud


## Allouer de l’espace sur le plan de démarrage et l’intégration du plan Pro

Pour tous les environnements de Formule de démarrage et le forfait Pro [Environnement d’intégration](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md), vous pouvez allouer plus d’espace pour MySQL dans le `.magento/services.yaml` en augmentant la variable `mysql: disk:` . Par exemple :

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Voir [Configuration du service MySQL](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_services-mysql.html) article à titre de référence.

Une fois que vous avez modifié `.magento/services.yaml` , vous devez valider et pousser vos modifications pour qu’elles soient appliquées. La notification push déclenche le processus de déploiement.

>[!WARNING]
>
>Une partition du plan de démarrage ne doit jamais être réduite (par exemple, de 30 à 20 Go), car cela va probablement entraîner une corruption catastrophique des données.

## Allouer de l’espace sur l’évaluation ou la production ProPlan

Pour apporter ces modifications à l’environnement d’évaluation ou de production du plan Pro, vous devez créer une [ticket de support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). Lors de l’envoi d’un ticket d’assistance pour augmenter le stockage, l’assistance devra savoir à quel niveau et à quelle partition le stockage doit être appliqué (`/mysql` ou `/exports`). Une demande d’augmentation du stockage nécessite l’approbation de votre équipe de compte d’Adobe, qui examinera la quantité de stockage que vous avez autorisée (selon le formulaire de commande) avant de la valider.

## Diminution de l’espace alloué non disponible (formule Pro et Starter)

Le support Adobe Commerce peut créer une partition (`/mysql` ou `/exports`), mais ne peut pas rétrécir une partition. Il y a un risque de corruption des données dans ce cas, c&#39;est pourquoi la diminution du stockage pour une partition n&#39;est pas disponible.
C&#39;est également vrai pour le plan Starter, où vous pouvez augmenter vous-même l&#39;espace alloué : réduire est fortement déconseillé et peut entraîner une corruption catastrophique des données.
