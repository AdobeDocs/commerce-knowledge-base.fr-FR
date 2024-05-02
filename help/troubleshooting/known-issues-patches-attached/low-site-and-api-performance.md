---
title: Faibles performances du site et de l’API
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.1 lié au fait que les performances du site et de l’API sont faibles suite au temps nécessaire pour écrire "debug.log".
exl-id: b71816cd-f580-4c80-9694-585ed051a56d
feature: REST, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Faibles performances du site et de l’API

Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.1 lié au fait que les performances du site et de l’API sont faibles en raison du temps nécessaire pour écrire. `debug.log`.

## Problème

Les performances du site sont lentes. Les opérations de l’API s’exécutent lentement, par exemple en mettant à jour les produits à l’aide de la variable `PUT` . Lorsque vous examinez de plus près les opérations utilisant New Relic, la plupart de la mémoire et du processeur sont consommés en écrivant sur `/var/log/debug.log`.

## Solution

Pour résoudre le problème, appliquez le correctif. Le correctif divise et écrit les journaux des méthodes de log, de paiement et d’expédition dans des fichiers distincts.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier ou cliquez sur le lien suivant :

[Téléchargez MDVA-8371\_EE\_2.2.1\_COMPOSER\_v2.patch.](assets/MDVA-8371_EE_2.2.1_COMPOSER_v2.patch.zip)

### Versions Adobe Commerce compatibles

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.2.1

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobes suivantes :

* Adobe Commerce sur l’infrastructure cloud 2.2.0, 2.2.2, 2.2.3
* Adobe Commerce on-premise 2.2.0, 2.2.2, 2.2.3

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
