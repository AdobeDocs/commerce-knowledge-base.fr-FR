---
title: Les tables MySQL sont trop grandes
description: Cet article explique pourquoi il s’agit d’un problème lorsqu’une table MySQL dépasse 1 Go et comment l’empêcher.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Les tables MySQL sont trop grandes

Cet article explique pourquoi il s’agit d’un problème lorsqu’une table MySQL dépasse 1 Go et comment l’empêcher.

## Produits et versions concernés :

* Adobe Commerce sur l’infrastructure cloud 2.x.x
* Adobe Commerce On-Premise 2.x.x

## Problème

La taille des tables MySQL n’a pas d’incidence directe sur les performances du site. Toutefois, si un tableau est volumineux, il peut être fréquemment utilisé pour insérer des données supplémentaires ou obsolètes. MySQL est conçu pour les bases de données, où le ratio entre les opérations de lecture/écriture est de 80 %/20 %.  Pour les tables volumineuses, 1 Go et plus, les index MySQL, conçus pour accélérer les performances lors des opérations de lecture, peuvent dégrader les performances lors des opérations d’écriture.

## Solution

Tenez compte des options suivantes pour éviter une baisse des performances :

* Créez une tâche CRON qui nettoie les tables volumineuses. Voir [Recherche de tables MySQL volumineuses](/help/how-to/general/find-large-mysql-tables.md) dans notre base de connaissances d’assistance pour obtenir des recommandations sur l’identification des tables volumineuses.
* Pour les tables de plus de 1 Go, utilisez un moteur MySQL optimisé pour l’écriture des logs. Par exemple, le moteur d’archivage.
* Mise à jour de la fonctionnalité afin d’éviter le stockage des journaux dans DB.

## Lecture connexe

[Des tables de journal des modifications surdimensionnées provoquant des retards dans les mises à jour des entités](/help/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront.md) dans notre base de connaissances de soutien.
