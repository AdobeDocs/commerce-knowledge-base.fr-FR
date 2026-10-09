---
title: 'PWA Studio : le navigateur ne peut pas résoudre le site .local.pwadev'
description: Cet article fournit une solution lorsqu’un autre programme ou processus a modifié votre [fichier hôte](https://en.wikipedia.org/wiki/Hosts_(file\) et supprimé l’entrée pour le domaine de votre projet.
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
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
source-wordcount: '255'
ht-degree: 0%
---
# PWA Studio : le navigateur ne peut pas résoudre le site .local.pwadev

Cet article fournit une solution lorsqu’un autre programme ou processus a modifié votre [fichier hôte]&#x200B;(https://en.wikipedia.org/wiki/Hosts_(file\)) et supprimé l’entrée pour le domaine de votre projet.

## Produits et versions concernés

PWA Studio pour Adobe Commerce

## Problème

Lorsque vous accédez au site de développement/d’évaluation, vous ne pouvez pas voir le site `.local.pwadev`.

## Cause

PWA Studio vous permet d’attribuer un nom d’hôte personnalisé et un certificat SSL pour votre projet à votre ordinateur local. Cela implique la création d’une nouvelle entrée dans le fichier hôte de votre ordinateur qui ressemble à `my-storefront-project-abc123.local.pwadev`.

Cette entrée indique à tout navigateur sur l’ordinateur du développeur de consulter le projet de storefront local lorsqu’il accède à cette URL. Si un autre programme ou processus est entré et a supprimé cette entrée, le navigateur ne saurait pas où aller et le navigateur ne peut pas résoudre le site `.local.pwadev`.

## Solution

Vous pouvez [modifier manuellement votre fichier d’hôte](https://docs.rackspace.com/docs/modify-your-hosts-file) pour ajouter l’entrée en retour, mais vous devez examiner l’autre logiciel installé pour voir ce qui a remplacé la modification précédente.

## Lectures connexes dans notre base de connaissances de support

* [PWA Studio : erreur d’approbation de certificat auto-signé](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio : le webpack se bloque avant de commencer la compilation](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio : le navigateur affiche l’erreur « Impossible de remplacer par »](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio : erreurs de validation lors de l’exécution du mode Développeur](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
