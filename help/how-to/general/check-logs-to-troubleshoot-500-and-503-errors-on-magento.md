---
title: Consultez les journaux pour résoudre les erreurs 500 et 503 sur Adobe Commerce
description: Cet article explique comment vérifier le fichier « access.log » et les journaux associés pour résoudre les erreurs 503 et 500, qui peuvent être dues à un trafic ou à des ressources insuffisantes du serveur. L’affichage du fichier « access.log » et des journaux associés peut fournir des informations sur ce qui peut causer des problèmes liés à Adobe Commerce sur l’infrastructure cloud.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: 66ac9de94e9a4a1eccdb5aac1875ecf0a0637e90
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Consultez les journaux pour résoudre les erreurs 500 et 503 sur Adobe Commerce

Cet article explique comment vérifier les `access.log` et les journaux associés pour résoudre les erreurs 503 et 500, qui peuvent être dues à un trafic ou à des ressources de serveur insuffisantes. L’affichage du `access.log` et des journaux associés peut fournir des informations sur les causes possibles des problèmes liés à Adobe Commerce sur l’infrastructure cloud.

<!--
Bob - not in TOC
-->

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, toutes les [versions prises en charge](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html?lang=fr).

Pour afficher les journaux de ces erreurs de serveur, vérifiez les `access.log` sur le serveur web, par exemple `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Pour vérifier les journaux associés :

1. Exécutez la commande suivante dans l’interface de ligne de commande si elle se trouve le jour même (pour Adobe Commerce sur l’infrastructure cloud, architecture de plan Pro). Ou jusqu’à un certain point dans le passé (pour Adobe Commerce sur l’architecture du plan de démarrage de l’infrastructure cloud), car la durée de couverture des journaux est limitée et la rotation des journaux n’est pas disponible : `grep -r "\" [50[0-9]" /path/to/access.log` Si l’erreur s’est produite dans le passé, exécutez la commande suivante dans l’interface de ligne de commande (architecture Pro uniquement) : `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Vérifiez ensuite les `exception.log` et `error.log` ou le [journal pivoté](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html?lang=fr#log-rotation) équivalent (journaux qui sont automatiquement pivotés et compressés lorsqu’ils atteignent une certaine taille de fichier) de la même date et heure afin de localiser l’erreur potentielle et de voir ce qui pouvait se produire et en être la cause. Remarque : pour vérifier le `exception.log` et `error.log` exécuter les commandes ci-dessus dans l’interface de ligne de commande, mais remplacez `access.log` par `exception.log` ou `error.log`.

## Lecture connexe

* Voir [Afficher et gérer les journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=fr) dans le *Guide d’Adobe Commerce sur les infrastructures cloud*.
* Consultez la section [Dépannage des erreurs 503](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) dans notre base de connaissances d’assistance.