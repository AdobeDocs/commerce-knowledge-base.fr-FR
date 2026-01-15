---
title: Problèmes de vérification de la préparation des dépendances des composants
description: Cet article fournit des solutions aux conflits de dépendance des composants.
exl-id: e0865226-2aaf-4bdd-8c28-28f32f38ce0c
feature: Configuration
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Problèmes de vérification de la préparation des dépendances des composants

Cet article fournit des solutions aux conflits de dépendance des composants.

## Résoudre les conflits de dépendance des composants {#resolve-component-dependency-conflicts}

Nous vous suggérons d’essayer les solutions suivantes dans l’ordre indiqué :

1. [Conflits de dépendances](#trouble-depend-conflict)
1. [Problèmes liés aux autorisations du système de fichiers](#trouble-depend-permission)
1. [Le statut de la vérification des dépendances des composants ne change jamais](#trouble-depend-state)

### Conflits de dépendances {#trouble-depend-conflict}

Le message *Nous avons trouvé des dépendances de composant en conflit* s’affiche si le compositeur ne peut pas déterminer les composants à installer ou à mettre à jour. Pour résoudre les problèmes de dépendance des composants, vous devez être une personne technique qui comprend parfaitement le fonctionnement du compositeur.

Voici un exemple de message d’échec :

```bash
We found conflicting component dependencies.
 You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
 We've detected conflicts with the following packages:
 - magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

>[!NOTE]
>
>Le message qui s’affiche sera probablement différent.

## Problèmes liés aux autorisations du système de fichiers {#trouble-depend-permission}

Si le propriétaire du système de fichiers Adobe Commerce ne dispose pas des autorisations d’écriture dans les répertoires du système de fichiers Adobe Commerce, un message similaire au suivant s’affiche :

```bash
file_put_contents(/var/www/html/magento2/var/composer_home/cache/repo/https---
packagist.org/provider-doctrine$instantiator.json): failed to open stream: Permission denied
```

Assurez-vous de définir les autorisations de système de fichiers comme décrit dans l’article [Présentation de la propriété et des autorisations](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) dans notre documentation destinée aux développeurs.

## Le statut de la vérification des dépendances des composants ne change jamais {#trouble-depend-state}

Dans certains cas, le statut de la vérification des dépendances du composant ne change pas, même après avoir tenté de corriger les problèmes. Dans ce cas, vous pouvez supprimer ou renommer les fichiers nommés `<magento_root>/var/.update_cronjob_status` et `<magento_root>/var/.setup_cronjob_status`, puis réessayer d’exécuter le Gestionnaire de composants.

Le changement de nom ou la suppression de ces fichiers force le Gestionnaire de composants à exécuter à nouveau les vérifications.
