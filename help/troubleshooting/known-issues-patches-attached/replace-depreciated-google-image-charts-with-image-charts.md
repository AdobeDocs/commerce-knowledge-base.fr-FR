---
title: Remplacer les graphiques Google dépréciés par les graphiques à images
description: La plupart des éditions et versions d’Adobe Commerce utilisent actuellement [Graphiques d’images Google](https://developers.google.com/chart/image/) pour effectuer le rendu de graphiques statiques dans les tableaux de bord d’administration. À compter du 14 mars 2019, Google cessera de prendre en charge les graphiques d’images Google. Pour résoudre ce problème, nous fournissons un correctif pour remplacer les graphiques d’images Google par le service gratuit [Graphiques d’images](https://www.image-charts.com/).
exl-id: f86f0bb9-8a03-471d-8696-1eba4b8acbd1
feature: Cache, Compliance
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Remplacer les graphiques Google dépréciés par les graphiques à images

La plupart des versions et éditions Adobe Commerce utilisent actuellement [Graphiques d’images Google](https://developers.google.com/chart/image/) pour effectuer le rendu des graphiques statiques dans les tableaux de bord d’administration. À compter du 14 mars 2019, Google cessera de prendre en charge les graphiques d’images Google. Pour résoudre ce problème, nous fournissons un correctif pour remplacer les graphiques Google avec [Graphiques d’images](https://www.image-charts.com/) service gratuit.

## Versions affectées

* Adobe Commerce 1.X, toutes les éditions
* Adobe Commerce 2.X, toutes les éditions

>[!NOTE]
>
>Adobe Commerce On-Premise 1.14.4.1, Magento Open Source 1.9.4.1, Adobe Commerce On-Premise et Adobe Commerce sur l’infrastructure cloud 2.3.2 incluront cette mise à jour du graphique. La mise à niveau vers ces versions continue la prise en charge des graphiques à images sans correctifs supplémentaires.

## Problème

Google a cessé de prendre en charge les graphiques d’images Google le 14 mars 2019. Les utilisateurs d’Adobe Commerce 1.X et d’Adobe Commerce 2.2.X de toutes les versions ne pourront pas afficher les graphiques statiques à moins de télécharger et d’appliquer le correctif, en remplaçant les Graphiques d’image Google par la solution de graphiques à images. Les graphiques affichés auront la même conception et la même fonctionnalité que les graphiques d’image Google grâce au service de compte libre Graphiques d’images avec une [RGPD](https://www.image-charts.com/data-processing-addendum.html) politique de confidentialité de la conformité. Pour connaître les autres options, voir [Graphiques d’images](https://www.image-charts.com/).

## Solution

Pour pouvoir afficher des graphiques statiques dans l’administrateur Commerce, téléchargez et appliquez le correctif fourni par Adobe Commerce. Aucune configuration supplémentaire n’est nécessaire.

### Adobe Commerce sur site

1. Enregistrez le [joint MAGETWO-98833\_compositeur\_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch.zip) corrigez et téléchargez-le dans votre répertoire racine Adobe Commerce.
1. Exécutez la commande SSH suivante, en remplaçant le nom du correctif par le nom réel :

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch
   ```

   Si la commande ci-dessus ne fonctionne pas, essayez d’utiliser `-p2` au lieu de `-p1`.)

1. Pour que les modifications soient répercutées, actualisez le cache dans l’Admin sous **Système** > **Gestion du cache**.

### Adobe Commerce sur l’infrastructure cloud

Pour les commerçants Cloud, le correctif sera inclus à la mise à jour des outils CEE la plus proche.

### Magento 2 Open Source

1. Accédez à [https://magento.com/tech-resources/download\#download2291](https://magento.com/tech-resources/download#download2291).
1. Dans le **Sélectionner votre format** , sélectionnez la version du compositeur et cliquez sur **Télécharger**.
1. Téléchargez le correctif dans votre répertoire racine Adobe Commerce.
1. Exécutez la commande SSH suivante, en remplaçant le nom du correctif par le nom réel :

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-37-48.patch
   ```

   (Si la commande ci-dessus ne fonctionne pas, essayez d’utiliser `-p2` au lieu de `-p1`.)

1. Pour que les modifications soient répercutées, actualisez le cache dans l’Admin sous **Système** > **Gestion du cache**.

### Adobe Commerce 1 sur site

Pour télécharger et appliquer le correctif, procédez comme suit :

1. Enregistrez le [joint MPERF-10509-EE-2019-03-13-06-32-19.diff](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff.zip) corrigez et téléchargez-le dans votre répertoire racine Adobe Commerce.
1. Exécutez la commande SSH suivante :

   ```git
   patch -p1 < MPERF-10509-EE-2019-03-13-06-32-19.diff
   ```

   (Si la commande ci-dessus ne fonctionne pas, essayez d’utiliser `-p2` au lieu de `-p1`.)

1. Pour que les modifications soient répercutées, actualisez le cache dans l’Admin sous **Système** > **Gestion du cache**.

### Magento 1 Open Source

Pour télécharger et appliquer le correctif, procédez comme suit :

1. Cliquez sur [**ce lien**](https://magento.com/tech-resources/download#download2283) pour localiser le correctif Graphiques du tableau de bord d’administration.
1. Sélectionner

   ```git
   MPERF-10509.diff
   ```

   de la **Sélectionner votre format** puis cliquez sur Télécharger.

1. Téléchargez le fichier dans le répertoire racine Adobe Commerce.
1. Exécutez la commande SSH suivante :

   ```git
   patch -p1 < MPERF-10509.diff
   ```

   (Si la commande ci-dessus ne fonctionne pas, essayez d’utiliser `-p2` au lieu de `-p1`.)

1. Pour que les modifications soient répercutées, actualisez le cache dans l’Admin sous **Système** > **Gestion du cache**.

## Fichiers attachés

[Téléchargez MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch.](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch)

[Téléchargez MPERF-10509-EE-2019-03-13-06-32-19.diffh](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff)
