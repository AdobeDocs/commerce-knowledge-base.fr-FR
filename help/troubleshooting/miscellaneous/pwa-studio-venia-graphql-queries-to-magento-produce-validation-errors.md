---
title: "PWA Studio : les requêtes Venia GraphQL vers Adobe Commerce produisent des erreurs de validation"
description: Cet article fournit des recommandations sur la manière de résoudre le problème où les requêtes GraphQL storefront Venia vers l’instance Adobe Commerce produisent des erreurs de validation.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studio : les requêtes Venia GraphQL vers Adobe Commerce produisent des erreurs de validation

Cet article fournit des recommandations sur la manière de résoudre le problème où les requêtes GraphQL storefront Venia vers l’instance Adobe Commerce produisent des erreurs de validation.

## Produits et versions concernés

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x
* Projet PWA Studio pour Adobe Commerce

## Problème

Les requêtes Venia GraphQL envoyées à Adobe Commerce sur site ou à Adobe Commerce sur l’infrastructure cloud produisent des erreurs de validation.

## Cause

L’une des raisons à l’origine du problème peut être que Venia et ses requêtes GraphQL ne sont pas synchronisées avec le schéma de l’instance Adobe Commerce connectée.

## Solution

Pour tester si vos requêtes sont à jour, exécutez la commande suivante à la racine du projet :

```bash
yarn run validate-queries
```

Un rapport de compatibilité s’affiche alors. Si vous avez des incompatibilités, vous devez mettre à niveau votre PWA Studio ou votre instance Adobe Commerce. Vérifiez les [Matrice de compatibilité Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) pour voir exactement les versions dont vous avez besoin.

Pour obtenir des instructions sur la mise à niveau, reportez-vous à la documentation suivante :

* Pour les mises à niveau de PWA Studio, recherchez la section &quot;Mise à niveau à partir d’une version précédente&quot; de la section [Notes de mise à jour de PWA](https://github.com/magento/pwa-studio/releases/) pour la version vers laquelle vous devez effectuer la mise à niveau.
* [Mise à niveau d’Adobe Commerce vers la version de l’infrastructure cloud](https://devdocs.magento.com/cloud/project/project-upgrade.html) dans notre documentation destinée aux développeurs
* [Mettre à niveau Adobe Commerce sur site (installé à l’aide de &quot;création-projet compositeur&quot; ou d’une archive)](https://devdocs.magento.com/guides/v2.3/comp-mgr/cli/cli-upgrade.html) dans notre documentation destinée aux développeurs
* [Mettre à niveau Adobe Commerce sur site (installé par le clonage du référentiel Adobe Commerce)](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/dev_update-magento.html) dans notre documentation destinée aux développeurs

## Lecture connexe

* [PWA Studio : Webpack se bloque avant de commencer la compilation](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) dans notre base de connaissances de soutien
* [PWA Studio : erreurs de validation lors de l’exécution du mode Développeur](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) dans notre base de connaissances de soutien
* [PWA Studio : le navigateur affiche l’erreur &quot;Impossible de remplacer par&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) dans notre base de connaissances de soutien
* [Configurer NPM pour pouvoir utiliser PWA Studio](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) dans notre base de connaissances de soutien
* [PWA pour la documentation Adobe Commerce](https://magento.github.io/pwa-studio/)
