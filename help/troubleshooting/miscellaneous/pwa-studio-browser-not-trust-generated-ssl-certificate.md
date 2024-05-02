---
title: "PWA Studio : navigateur pas approuvé le certificat SSL"
description: Cet article fournit une solution à un avertissement de certificat SSL généré et non approuvé dans votre navigateur lorsque vous accédez à une instance locale de votre vitrine de PWA Studio pendant le développement.
exl-id: b7bfe1e6-5832-4472-9e51-f04b8583428a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# PWA Studio : le navigateur n’a pas approuvé le certificat SSL généré

Cet article fournit une solution à un avertissement de certificat SSL généré et non approuvé dans votre navigateur lorsque vous accédez à une instance locale de votre vitrine de PWA Studio pendant le développement.

## Produits et versions concernés

PWA Studio pour Adobe Commerce

## Problème

Le navigateur n’fait pas confiance au certificat SSL généré de votre vitrine de PWA Studio locale.

## Cause

Accès au site de développement/d’évaluation.

## Solution

Dans votre projet storefront, exécutez la commande pour ajouter un nom d’hôte personnalisé et un certificat SSL à votre instance de développement locale :

```sh
yarn buildpack create-custom-origin ./
```

La génération des certificats est gérée par [devcert](https://github.com/davewasmer/devcert). Elle dépend d’OpenSSL. Vérifiez donc que vous disposez d’une version actuelle d’openssl sur votre système à l’aide de la commande suivante :

`openssl version`

La version doit être 1.0 ou supérieure (ou LibreSSL 2, dans le cas d&#39;OSX High Sierra).

Vous pouvez installer des versions plus élevées d’OpenSSL avec [Homebrew](https://brew.sh/) sur OSX, [Chocolatey](https://chocolatey.org/) sous Windows ou le gestionnaire de modules de votre distribution Linux.

Si vous exécutez Linux, assurez-vous que la variable `libnss3-tools` (ou l’équivalent) est installé sur votre système. Informations supplémentaires fournies dans cette section du [devcert](https://github.com/davewasmer/devcert#skipcertutil) Lisez-moi.

Certains utilisateurs ont suggéré de supprimer le dossier de l’appareil pour déclencher la régénération du certificat.

* Pour les utilisateurs de MacOS, ce dossier se trouve généralement à l’adresse : `{{~/Library/Application Support/devcert }}`
* Pour les utilisateurs de Windows, ce dossier se trouve généralement à l’adresse : `${User}\AppData\Local\devcert`

## Lecture connexe dans notre base de connaissances de soutien

* [PWA Studio : erreur de confiance de certificat auto-signée](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio : Webpack se bloque avant de commencer la compilation](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio : le navigateur affiche l’erreur &quot;Impossible de remplacer par&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio : erreurs de validation lors de l’exécution du mode Développeur](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
