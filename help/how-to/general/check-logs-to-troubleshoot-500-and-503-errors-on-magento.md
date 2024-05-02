---
title: Consultez les journaux pour résoudre les erreurs 500 et 503 sur Adobe Commerce.
description: Cet article explique comment vérifier le fichier access.log et les journaux associés pour résoudre les erreurs 503 et 500, qui peuvent être causées par le trafic ou des ressources de serveur insuffisantes. L’affichage de "access.log" et des journaux associés peut fournir des informations sur ce qui peut causer des problèmes liés à Adobe Commerce sur l’infrastructure cloud.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Consultez les journaux pour résoudre les erreurs 500 et 503 sur Adobe Commerce.

Cet article explique comment vérifier la variable `access.log` et les journaux associés pour résoudre les erreurs 503 et 500, qui peuvent être causées par du trafic ou des ressources de serveur insuffisantes. Affichage de la `access.log` et les journaux associés peuvent fournir des informations sur les causes possibles des problèmes liés à Adobe Commerce sur l’infrastructure cloud.

<!--
Bob - not in TOC
-->

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, tous [versions prises en charge](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

Pour afficher les journaux de ces erreurs de serveur, cochez la case `access.log` sur le serveur web, par exemple : `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Pour vérifier les logs associés :

1. Exécutez la commande suivante dans l’interface de ligne de commande si elle est en cours (pour l’architecture de plan Adobe Commerce on cloud infrastructure Pro). Ou jusqu’à un certain point dans le passé (pour Adobe Commerce sur l’architecture du plan de démarrage de l’infrastructure cloud), puisque la durée de la couverture des journaux est limitée et que la rotation des journaux n’est pas disponible : `grep -r "\" [50[0-9]" /path/to/access.log` Si l’erreur s’est produite dans le passé, exécutez la commande suivante dans l’interface de ligne de commande (architecture Pro uniquement) : `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Cochez ensuite la case `exception.log` et `error.log` ou l’équivalent [journal pivoté](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) (journaux qui sont automatiquement pivotés et compressés lorsqu’ils atteignent une certaine taille de fichier) pour un même horodatage afin de localiser l’erreur potentielle et de voir ce qui s’est produit pour l’avoir provoquée. Remarque : Pour vérifier la variable `exception.log` et `error.log` Exécutez les commandes ci-dessus dans l’interface de ligne de commande, mais remplacez `access.log` avec `exception.log` ou `error.log`.

## Lecture connexe

* Voir [Affichage et gestion des journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) dans le *Guide d’infrastructure d’Adobe Commerce on Cloud*.
* Voir [Résolution des problèmes 503](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) dans notre base de connaissances de soutien.
* Voir [Dépannage du site Magento](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) dans notre base de connaissances de soutien.
