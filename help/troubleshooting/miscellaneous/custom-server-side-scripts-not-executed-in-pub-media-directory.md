---
title: Scripts côté serveur personnalisés non exécutés dans le répertoire des médias publics
description: Cet article fournit un correctif pour les scripts personnalisés côté serveur qui ne sont pas exécutés s’ils sont placés dans le répertoire `./pub/media/` de votre application Adobe Commerce sur l’infrastructure cloud. Il s’agit d’une limitation de sécurité attendue, car le répertoire « ./pub/media/ » est accessible en écriture. Pour rendre les scripts exécutables, placez-les dans des répertoires non inscriptibles, tels que `./app/code/` ou `./pub/`.
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%
---
# Scripts côté serveur personnalisés non exécutés dans le répertoire des médias publics

Cet article fournit un correctif pour les scripts personnalisés côté serveur qui ne sont pas exécutés s’ils sont placés dans le répertoire `./pub/media/` de votre application Adobe Commerce sur une infrastructure cloud. Il s’agit d’une limitation de sécurité attendue, car le répertoire `./pub/media/` est accessible en écriture. Pour rendre les scripts exécutables, placez-les dans des répertoires non inscriptibles, tels que `./app/code/` ou `./pub/`.

## Versions affectées

* Adobe Commerce sur les infrastructures cloud : 2.1.x et versions ultérieures, Starter et Pro planifie l’architecture, les architectures Wings et Legacy

## Problème : scripts non exécutés

Les scripts personnalisés côté serveur ne peuvent pas être exécutés lors de leur lancement.

Par exemple, lorsque l’utilisateur final (Adobe Commerce shopper) clique sur le lien menant au fichier `\*.php` avec le script (comme *domain.com/media/directory/script.php* ), le script est téléchargé au lieu d’être exécuté.

## Cause : emplacement incorrect du fichier de script

Le problème se produit lorsque les fichiers de script se trouvent dans le répertoire `./pub/media/` de l’application Adobe Commerce sur l’infrastructure cloud. Il s’agit d’un comportement attendu : en raison de limitations de sécurité, les fichiers des répertoires accessibles en écriture (`./pub/media/`) ne sont jamais exécutés.

## Solution : placez les scripts dans des répertoires non inscriptibles

Stocker les scripts côté serveur dans des répertoires non inscriptibles, tels que `./app/code/` ou `./pub/` «

## Documentation connexe

* [Cloud for Adobe Commerce > Structure de projet > Répertoires modifiables](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/project/file-structure#writable-directories) dans notre documentation destinée aux développeurs.
