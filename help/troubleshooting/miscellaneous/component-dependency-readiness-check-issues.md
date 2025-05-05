---
title: Problèmes de contrôle de l’état de préparation des dépendances des composants
description: Cet article fournit des solutions aux conflits de dépendance de composants.
exl-id: e0865226-2aaf-4bdd-8c28-28f32f38ce0c
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Problèmes de contrôle de l’état de préparation des dépendances des composants

Cet article fournit des solutions aux conflits de dépendance de composants.

## Résolution des conflits de dépendance de composant {#resolve-component-dependency-conflicts}

Nous vous suggérons d’essayer les solutions suivantes dans l’ordre indiqué :

1. [Dépendances conflictuelles](#trouble-depend-conflict)
1. [Problèmes d’autorisation du système de fichiers](#trouble-depend-permission)
1. [L’état de vérification de la dépendance des composants ne change jamais.](#trouble-depend-state)

### Dépendances conflictuelles {#trouble-depend-conflict}

Le message *Nous avons trouvé des dépendances de composants conflictuelles* s’affiche si le compositeur ne peut pas déterminer les composants à installer ou à mettre à jour. Pour résoudre les problèmes de dépendance de composant, vous devez être une personne technique qui comprend parfaitement le fonctionnement du compositeur.

Voici un exemple de message d’échec :

```bash
We found conflicting component dependencies.
 You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
 We've detected conflicts with the following packages:
 - magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

>[!NOTE]
>
>Le message que vous voyez sera probablement différent.

Reportez-vous à la section [Dépendances de composants en conflit pour une solution](/help/troubleshooting/miscellaneous/conflicting-component-dependencies.md) dans notre base de connaissances de support.

## Problèmes d’autorisation du système de fichiers {#trouble-depend-permission}

Si le propriétaire du système de fichiers Adobe Commerce ne dispose pas des autorisations nécessaires pour écrire dans les répertoires du système de fichiers Adobe Commerce, un message similaire à celui-ci s’affiche :

```bash
file_put_contents(/var/www/html/magento2/var/composer_home/cache/repo/https---
packagist.org/provider-doctrine$instantiator.json): failed to open stream: Permission denied
```

Veillez à définir les autorisations du système de fichiers comme décrit dans l’article [Présentation de la propriété et des autorisations](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) de notre documentation destinée aux développeurs.

## L’état de vérification de la dépendance des composants ne change jamais. {#trouble-depend-state}

Dans certains cas, l’état de la vérification de dépendance des composants ne change pas, même après avoir essayé de corriger les problèmes. Dans ce cas, vous pouvez supprimer ou renommer les fichiers nommés `<magento_root>/var/.update_cronjob_status` et `<magento_root>/var/.setup_cronjob_status` et essayer de réexécuter le Gestionnaire de composants.

Le changement de nom ou la suppression de ces fichiers force le Gestionnaire de composants à exécuter à nouveau les vérifications.
