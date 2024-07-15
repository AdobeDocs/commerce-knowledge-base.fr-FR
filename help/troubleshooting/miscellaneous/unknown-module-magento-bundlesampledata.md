---
title: Module inconnu Magento_BundleSampleData
description: Cet article fournit un correctif pour l’erreur de module inconnue lors de l’installation d’Adobe Commerce.
exl-id: c927bc8f-d70b-4305-87c1-223001212555
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Module inconnu Magento_BundleSampleData

Cet article fournit un correctif pour l’erreur de module inconnue lors de l’installation d’Adobe Commerce.

## Problème {#details}

Pendant l’installation, un message similaire à celui-ci s’affiche :

```text
[ERROR] exception 'LogicException' with message 'Unknown module in the requested list: 'Magento_BundleSampleData''
```

## Solution {#solution}

Essayez chacun des éléments suivants à la fois, puis réessayez l’installation.

1. Exécutez l’assistant de configuration web. Les modules sont répertoriés dans **Configurations de modules avancés**. Pour désactiver le module **Magento\_BundleSampleData**, décochez la case **Magento\_BundleSampleData** comme le montre la figure suivante.

   ![tshot_bundlesampledata.png](assets/tshoot_bundlesampledata.png)

1. Effacez l’historique et les données de tous les navigateurs de votre navigateur web.
1. Si vous disposez de Chrome, effacez toutes les données de navigateur liées à votre site.  Accédez à **Paramètres** > **Options avancées** > **Confidentialité** > **Paramètres de contenu** > **Tous les cookies et données de site**. Dans la colonne Site, cliquez sur l’adresse de votre serveur Adobe Commerce et cliquez sur **Tout supprimer**.
