---
title: '"Erreur "L’application de mise à jour n’est pas disponible""'
description: Cet article décrit la solution du problème "L’application de mise à jour n’est pas disponible" que vous pouvez rencontrer lors de la tentative de mise à jour/installation d’Adobe Commerce sur site à l’aide de l’assistant de configuration web.
exl-id: 85e55ed8-0bc9-4378-b722-46be98ce2638
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Erreur &quot;L’application de mise à jour n’est pas disponible&quot;

Cet article décrit la solution du problème &quot;L’application de mise à jour n’est pas disponible&quot; que vous pouvez rencontrer lors de la tentative de mise à jour/installation d’Adobe Commerce sur site à l’aide de l’assistant de configuration web.

## Problème

Le message suivant est affiché dans la vérification de préparation :

![Screen_Shot_2019-08-29_at_1.39.12_PM.png](assets/Screen_Shot_2019-08-29_at_1.39.12_PM.png)

## Produits/versions concernés

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Solution

Pour résoudre ce problème, vérifiez s’il existe un répertoire `<magento_root>/update` contenant des fichiers et des sous-répertoires. Sinon, voir [Configuration de la mise à jour](https://devdocs.magento.com/guides/v2.3/comp-mgr/updater/update-updater.html) dans notre documentation destinée aux développeurs.
