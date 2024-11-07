---
title: Fichier de configuration manquant ou modifié
description: Résolvez le problème lié à l’absence ou à la modification du fichier de configuration pour Adobe Commerce.
exl-id: d80bf981-8ba6-4357-a841-57bf5d3f2a3f
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Fichier de configuration manquant ou modifié

Cet article explique comment résoudre le problème de modification ou d’absence de vos fichiers de configuration.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions

## Problème

Les fichiers de configuration `config.php` et/ou `env.php` ont été modifiés incorrectement ou sont manquants.

## Solution

Le processus de déploiement crée un fichier de sauvegarde pour chaque fichier de configuration :

* `app/etc/config.php.bak` : contient des paramètres spécifiques au système et est généré automatiquement lors de la génération si elle n’existe pas.
* `app/etc/env.php.bak` — contient des données de configuration sensibles

Vous pouvez les restaurer à l&#39;aide de la commande CEE-outils `backup:restore` .

Les fichiers BAK sont un produit du processus de déploiement. Si vous modifiez manuellement un fichier de configuration après le déploiement, vos modifications ne sont pas répercutées dans les fichiers BAK existants.

Pour restaurer les fichiers de configuration :

1. Connectez-vous à votre référentiel distant à l’aide de [SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh).
1. Liste des fichiers de sauvegarde disponibles.

   ```
   ./vendor/bin/ece-tools backup:list
   ```

   ```
   The list of backup files:
   app/etc/env.php
   app/etc/config.php
   ```

1. Restaurez les fichiers de configuration.

   ```
   ./vendor/bin/ece-tools backup:restore
   ```

   Vous recevez la liste des fichiers de configuration existants affectés par la restauration.

   ```
   app/etc/env.php file exists! If you want to rewrite existed files use --force
   app/etc/config.php file exists! If you want to rewrite existed files use --force
   ```

1. Utilisez l’option `--force` pour remplacer tous les fichiers.

   ```
   ./vendor/bin/ece-tools backup:restore --force
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/env.php was restored.
   Backup file app/etc/config.php was restored.
   ```

1. Vous pouvez éventuellement restaurer un fichier de configuration spécifique.

   ```
   ./vendor/bin/ece-tools backup:restore --force --file=app/etc/config.php
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/config.php was restored.
   ```
