---
title: 'PWA Studio : le navigateur n’approuve pas le certificat SSL généré'
description: Cet article fournit une solution à un avertissement de certificat SSL généré non approuvé dans votre navigateur lorsque vous accédez à une instance locale de votre storefront PWA Studio pendant le développement.
exl-id: b7bfe1e6-5832-4472-9e51-f04b8583428a
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%
---
# PWA Studio : le navigateur n’approuve pas le certificat SSL généré

Cet article fournit une solution à un avertissement de certificat SSL généré non approuvé dans votre navigateur lorsque vous accédez à une instance locale de votre storefront PWA Studio pendant le développement.

## Produits et versions concernés

PWA Studio pour Adobe Commerce

## Problème

Le navigateur n’approuve pas le certificat SSL généré par votre storefront PWA Studio local.

## Cause

Accédez au site de développement/d’évaluation.

## Solution

Dans votre projet storefront, exécutez la commande pour ajouter un nom d’hôte personnalisé et un certificat SSL à votre instance de développement locale :

```sh
yarn buildpack create-custom-origin ./
```

La génération des certificats est gérée par [devcert](https://github.com/davewasmer/devcert). Cela dépend d’OpenSSL. Assurez-vous donc de disposer d’une version actuelle d’openssl sur votre système à l’aide de la commande suivante :

`openssl version`

La version doit être 1.0 ou supérieure (ou LibreSSL 2, dans le cas d’OSX High Sierra).

Vous pouvez installer des versions supérieures d’OpenSSL avec [Homebrew](https://brew.sh/) sous OSX, [Chocolatey](https://chocolatey.org/) sous Windows ou le gestionnaire de packages de votre distribution Linux.

Si vous exécutez Linux, assurez-vous que `libnss3-tools` (ou l’équivalent) est installé sur votre système. Pour plus d’informations, reportez-vous à cette section du fichier lisez-moi [devcert](https://github.com/davewasmer/devcert#skipcertutil).

Certains utilisateurs ont suggéré de supprimer le dossier devcert pour déclencher la régénération du certificat.

* Pour les utilisateurs de MacOS, ce dossier se trouve généralement à l’adresse : `{{~/Library/Application Support/devcert }}`
* Pour les utilisateurs de Windows, ce dossier se trouve généralement à l’emplacement suivant : `${User}\AppData\Local\devcert`

## Lectures connexes dans notre base de connaissances de support

* [PWA Studio : erreur d’approbation de certificat auto-signé](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio : le webpack se bloque avant de commencer la compilation](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio : le navigateur affiche l’erreur « Impossible de remplacer par »](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio : erreurs de validation lors de l’exécution du mode Développeur](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
