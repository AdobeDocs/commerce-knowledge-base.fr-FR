---
title: Scripts côté serveur personnalisés non exécutés dans le répertoire de média publicitaire
description: Cet article fournit un correctif pour les cas où les scripts personnalisés côté serveur ne sont pas exécutés s’ils sont placés dans le `.Répertoire /pub/media/` de votre application Adobe Commerce sur l’infrastructure cloud. Il s’agit d’une limitation de sécurité attendue, puisque le ` .Le répertoire /pub/media/` peut être écrit. Pour rendre les scripts exécutables, placez-les dans des répertoires non modifiables, tels que `./app/code/` ou `./pub/`.
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Scripts côté serveur personnalisés non exécutés dans le répertoire de média publicitaire

Cet article fournit un correctif pour les cas où les scripts personnalisés côté serveur ne sont pas exécutés s’ils sont placés dans le répertoire `./pub/media/` de votre application Adobe Commerce sur l’infrastructure cloud. Il s’agit d’une limitation de sécurité attendue, car le répertoire `./pub/media/` peut être écrit. Pour rendre les scripts exécutables, placez-les dans des répertoires non modifiables, tels que `./app/code/` ou `./pub/`.

## Versions affectées

* Adobe Commerce sur l’infrastructure cloud : 2.1.x et versions ultérieures, Starter et Pro planifient l’architecture, les ailes et les architectures héritées

## Problème : scripts non exécutés

Les scripts personnalisés côté serveur ne peuvent pas être exécutés à l’exécution.

Par exemple, lorsque l’utilisateur final (client Adobe Commerce) clique sur le lien qui mène au fichier `\*.php` avec le script (comme *domain.com/media/directory/script.php* ), le script est téléchargé au lieu d’être exécuté.

## Cause : emplacement incorrect du fichier de script

Le problème se produit lorsque les fichiers de script se trouvent dans le répertoire `./pub/media/` de l’application Adobe Commerce sur l’infrastructure cloud. Ce comportement est attendu : en raison de limitations de sécurité, les fichiers des répertoires modifiables (`./pub/media/`) ne sont jamais exécutés.

## Solution : placer des scripts dans des répertoires non modifiables

Stocker les scripts côté serveur dans des répertoires non modifiables, tels que `./app/code/` ou `./pub/`

## Documentation connexe

* [Cloud pour Adobe Commerce > Structure de projet > Répertoires modifiables](https://devdocs.magento.com/guides/v2.3/cloud/project/project-start.html#write-dir) dans notre documentation destinée aux développeurs.
