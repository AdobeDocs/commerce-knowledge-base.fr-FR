---
title: Mettre à jour les rapports avancés pour qu’ils s’exécutent sur son propre groupe cron
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.3.0 où les rapports avancés n’affichent aucune donnée. Cela est dû au fait que la tâche de création de rapports avancée "analytics_collect_data" n’est pas exécutée conformément au planning. Cet article fournit un correctif qui crée un groupe cron de création de rapports avancés "analytics".
exl-id: 8aff9e2b-d9be-4136-975b-05963e23f55c
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Mettre à jour les rapports avancés pour qu’ils s’exécutent sur son propre groupe cron

Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.3.0 où les rapports avancés n’affichent aucune donnée. Cela est dû au fait que la tâche de création de rapports avancée `analytics_collect_data` n’est pas exécutée conformément au planning. Cet article fournit un correctif qui crée un groupe cron de création de rapports avancés `analytics`.

## Problème

Aucune donnée n’est chargée dans le module de reporting avancé.

## Correctif

Le correctif est joint à cet article. Le correctif déplace les tâches de la tâche cron `analytics` du groupe par défaut vers `analytics`.

Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[MDVA-19640\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-19640_EE_2.3.0_COMPOSER_v1.patch.zip)

Après avoir appliqué le correctif, exécutez la requête SQL suivante. La requête doit être exécutée pour modifier les enregistrements dans la table `cron_schedule`.

```
UPDATE core_config_data
SET `path` = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics")
WHERE `path` LIKE "crontab/default/jobs/analytics%";
```

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour

* Adobe Commerce sur l’infrastructure cloud 2.3.0

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes : 2.2.2-2.2.10, 2.3.0-2.3.2 et 2.3.2-p2 et 2.3.3, pour Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
