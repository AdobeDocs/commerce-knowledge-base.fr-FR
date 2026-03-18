---
title: 'PWA Studio : le webpack se bloque avant de commencer la compilation'
description: Cet article parle d’une solution suggérée pour le moment où un javascript [Webpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack) reste bloqué pendant longtemps avant de commencer la compilation dans Progressive Web App Studio (PWA Studio).
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 032fe4d32921c63570672b9c68e8c03e00bd1077
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# PWA Studio : le webpack se bloque avant de commencer la compilation

Cet article parle d’une solution suggérée pour le cas où un javascript [Webpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack) se bloquerait longtemps avant de commencer la compilation dans Progressive Web App Studio (PWA Studio).

## Produits et versions concernés

* PWA Studio

## Problème

[Consultez la dernière version de pwa-buildpack](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack) et le

```yaml
pwa-buildpack
```

le numéro de version est placé à côté de la liste des noms de fichier `package.json`. Si vous disposez d’une ancienne version de

```yaml
pwa-buildpack
```

projet, le webpack peut être bloqué pendant longtemps avant de commencer la compilation.

<u>Procédure à suivre </u> :

<u>Conditions préalables </u> : configurez un storefront PWA Studio, tel que Venia, avec une instance Adobe Commerce locale et exécutez une

```yaml
build
```

ou

```yaml
watch
```

commande.

<u>Résultat attendu </u> :

* Si vous utilisez le    ```yaml    build    ```    génère normalement les artefacts de build pour Venia.
* Si vous utilisez le    ```yaml    watch    ```    , démarre normalement le storefront Venia.

<u>Résultat réel</u> :

Votre

```yaml
build
```

ou

```yaml
watch
```

La commande semble bloquée et ne se termine pas, et aucune erreur ne s’affiche.

## Solutions

Mettez à jour votre projet à l’aide de la commande suivante :

```yaml
yarn upgrade
```

Vérifiez que vous disposez d’une version actuelle d’openssl sur votre système à l’aide de la commande suivante :

```yaml
openssl version
```

La version doit être 1.0 ou supérieure (ou LibreSSL 2, dans le cas d’OSX High Sierra.).

Vous pouvez installer des versions supérieures d’OpenSSL avec [Homebrew](https://brew.sh/) sous OSX, [Chocolatey](https://chocolatey.org/) sous Windows ou le gestionnaire de packages de votre distribution Linux.

## Lecture connexe

* [Javascript Webpack : Concepts](https://webpack.js.org/concepts/)
* [Configuration du storefront Venia](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
* [PWA Buildpack](https://developer.adobe.com/commerce/pwa-studio/guides/packages/buildpack/)
* [Interface de ligne de commande buildpack](https://developer.adobe.com/commerce/pwa-studio/api/buildpack/cli/)
* [Outils et bibliothèques : buildpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack)
