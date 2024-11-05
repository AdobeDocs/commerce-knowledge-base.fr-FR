---
title: '[!DNL MySQL] tables trop volumineuses'
description: Cet article explique pourquoi il s’agit d’un problème lorsqu’une table [!DNL MySQL] dépasse 1 Go et comment l’empêcher.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL MySQL] tables trop volumineuses

Cet article explique pourquoi il s’agit d’un problème lorsqu’une table [!DNL MySQL] dépasse 1 Go et comment l’empêcher.

## Produits et versions concernés :

* Adobe Commerce sur l’infrastructure cloud 2.x.x
* Adobe Commerce On-Premise 2.x.x

## Problème

La taille des tables [!DNL MySQL] n’affecte pas directement les performances du site. Toutefois, si un tableau est volumineux, il peut être fréquemment utilisé pour insérer des données supplémentaires ou obsolètes. [!DNL MySQL] est conçu pour les bases de données, dont le ratio entre les opérations de lecture/écriture est de 80 %/20 %.  Pour les tables volumineuses, 1 Go et plus, les index [!DNL MySQL], conçus pour accélérer les performances lors des opérations de lecture, peuvent dégrader les performances lors des opérations d’écriture.

## Solution

Tenez compte des options suivantes pour éviter une baisse des performances :

* Créez une tâche CRON qui nettoie les tables volumineuses. Pour obtenir des recommandations sur la manière d’identifier les tables volumineuses, reportez-vous à la section [Rechercher les tables volumineuses [!DNL MySQL] 2} de notre base de connaissances de support.](/help/how-to/general/find-large-mysql-tables.md)
* Pour les tables de plus de 1 Go, utilisez un moteur [!DNL MySQL] optimisé pour l’écriture de journaux. Par exemple, le moteur d’archivage.
* Mise à jour de la fonctionnalité afin d’éviter le stockage des journaux dans DB.

## Lecture connexe

* [ Tables de logs de modifications surdimensionnées provoquant des retards dans les mises à jour des entités ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront) dans notre base de connaissances de support
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
