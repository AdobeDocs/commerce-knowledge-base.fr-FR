---
title: "PWA Studio : Webpack se bloque avant de commencer la compilation"
description: Cet article parle d’une solution suggérée lorsqu’un JavaScript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) se bloque longtemps avant de commencer la compilation dans Progressive Web App Studio (PWA Studio).
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# PWA Studio : Webpack se bloque avant de commencer la compilation

Cet article décrit une solution suggérée pour le moment où un JavaScript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) se bloque longtemps avant de commencer la compilation dans Progressive Web App Studio (PWA Studio).

## Produits et versions concernés

* PWA Studio

## Problème

[Vérifiez quelle est la dernière version de pwa-buildpack.](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack), et la variable

```yaml
pwa-buildpack
```

Le numéro de version est en regard de la variable `package.json` liste des noms de fichier. Si vous disposez d’une ancienne version de la variable

```yaml
pwa-buildpack
```

, le webpack peut être suspendu pendant longtemps avant de commencer la compilation.

<u>Étapes à reproduire</u>:

<u>Conditions préalables</u>: configurez une vitrine de PWA Studio, telle que Venia, avec une instance Adobe Commerce locale et exécutez une

```yaml
build
```

ou

```yaml
watch
```

.

<u>Résultat attendu</u>:

* Si vous utilisez la variable    ```yaml    build    ```    , elle génère normalement les artefacts de version pour Venia.
* Si vous utilisez la variable    ```yaml    watch    ```    , il démarre normalement le storefront Venia.

<u>Résultat réel</u>:

Votre

```yaml
build
```

ou

```yaml
watch
```

semble bloquée et ne se termine pas, aucune erreur ne s’affiche.

## Solutions

Mettez à jour votre projet à l’aide de la commande suivante :

```yaml
yarn upgrade
```

Vérifiez que votre système dispose d’une version actuelle d’openssl à l’aide de la commande suivante :

```yaml
openssl version
```

La version doit être 1.0 ou supérieure (ou LibreSSL 2, dans le cas d&#39;OSX High Sierra).

Vous pouvez installer des versions plus élevées d’OpenSSL avec [Homebrew](https://brew.sh/) sur OSX, [Chocolatey](https://chocolatey.org/) sous Windows ou le gestionnaire de modules de votre distribution Linux.

## Lecture connexe

* [Webpack JavaScript : concepts](https://webpack.js.org/concepts/)
* [Configuration de la vitrine Venia](https://magento.github.io/pwa-studio/venia-pwa-concept/setup/)
* [PWA Buildpack](https://magento.github.io/pwa-studio/pwa-buildpack/)
* [Interface de ligne de commande de buildpack](https://magento.github.io/pwa-studio/pwa-buildpack/reference/buildpack-cli/)
* [Outils et bibliothèques : buildpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)
