---
title: "PWA Studio : le navigateur ne peut pas résoudre le site .local.pwadev"
description: Cet article fournit une solution lorsque un autre programme ou processus a modifié votre [fichier hôte] (https://en.wikipedia.org/wiki/Hosts_(file) et supprimé l’entrée pour votre domaine de projet.
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# PWA Studio : le navigateur ne peut pas résoudre le site .local.pwadev

Cet article fournit une solution lorsque un autre programme ou processus a modifié votre [fichier hôte] (https://en.wikipedia.org/wiki/Hosts_(file\) et supprimé l’entrée pour votre domaine de projet.

## Produits et versions concernés

PWA Studio pour Adobe Commerce

## Problème

Lorsque vous accédez au site de développement/d’évaluation, vous ne pouvez pas voir le site `.local.pwadev`.

## Cause

PWA Studio vous permet d’attribuer un nom d’hôte personnalisé et un certificat SSL pour votre projet à votre ordinateur local. Cela implique de créer une nouvelle entrée dans le fichier d’hôte de votre ordinateur qui ressemble à `my-storefront-project-abc123.local.pwadev`.

Cette entrée indique à n’importe quel navigateur de l’ordinateur du développeur d’examiner le projet storefront local lorsqu’il accède à cette URL. Si un autre programme ou processus est entré et a supprimé cette entrée, le navigateur ne sait pas où aller et le navigateur ne peut pas résoudre le site `.local.pwadev`.

## Solution

Vous pouvez [modifier manuellement votre fichier d’hôtes](https://support.rackspace.com/how-to/modify-your-hosts-file/) pour ajouter l’entrée en retour, mais vous devez examiner votre autre logiciel installé pour voir ce qui a écrasé la modification précédente.

## Lecture connexe dans notre base de connaissances de soutien

* [PWA Studio : erreur de confiance de certificat auto-signée](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio : Webpack se bloque avant de commencer la compilation](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio : le navigateur affiche l’erreur &quot;Impossible de remplacer par&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio : erreurs de validation lors de l’exécution du mode Développeur](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
