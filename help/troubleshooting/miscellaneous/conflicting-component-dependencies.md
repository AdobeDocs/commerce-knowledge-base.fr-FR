---
title: Conflits de dépendances des composants
description: Cet article fournit une solution pour les dépendances de composants conflictuelles. Lors de la configuration ou de la mise à jour d’Adobe Commerce à l’aide de l’assistant de configuration web, le message d’erreur du compositeur *"Nous avons détecté des dépendances de composants conflictuelles"* s’affiche.
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 8f0f7412e75e07a22e66236b88c095c698dbf23e
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Conflits de dépendances des composants

Cet article fournit une solution pour les dépendances de composants conflictuelles. Lorsque vous essayez de configurer ou de mettre à jour Adobe Commerce à l’aide de l’assistant de configuration web, le *&quot;Nous avons trouvé des dépendances de composants conflictuelles&quot;* Message d’erreur du compositeur.

## Produits et versions concernés

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Problème {#issue}

Un message d’erreur de dépendances des composants en conflit similaire à ce qui suit (les noms et versions réels du package varient) :

```bash
We found conflicting component dependencies.
You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
We have detected conflicts with the following packages:
- magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

## Cause

Ce message s’affiche si le compositeur ne peut pas déterminer les composants à installer ou à mettre à jour.

## Solution

Deux scénarios principaux peuvent entraîner des conflits de dépendances des composants. Cliquez sur votre scénario pour obtenir les étapes de dépannage.

* [Mise à niveau d’Adobe Commerce](#upgrading-magento)
* [Incompatibilité avec les modules tiers :](#incompatibility-third-party-modules)
   * [Adobe Commerce (tous les types de déploiement)](#magento-commerce-magento-commerce-cloud)
   * [Magento Open Source](#opensource)

## Mise à niveau d’Adobe Commerce {#upgrading-magento}

Si vous effectuez une mise à niveau d’Adobe Commerce sur l’infrastructure cloud, essayez de résoudre les conflits de dépendances de composant :

* Vérifiez les clés utilisées pour la mise à niveau. Les clés sont-elles générées à partir du compte de messagerie approprié ?
* Vérifiez les autorisations et assurez-vous qu’elles correspondent aux exigences de mise à niveau du Magento. Réviser [Présentation de la mise à niveau du Magento > Liste de contrôle de mise à jour et de mise à niveau > Autorisations du système de fichiers](https://devdocs.magento.com/guides/v2.3/comp-mgr/prereq/prereq_compman-checklist.html#perms) dans notre documentation destinée aux développeurs.

## Incompatibilité avec les modules tiers : {#incompatibility-third-party-modules}

Les dépendances de composants en conflit peuvent également être causées par des modules tiers qui dépendent de composants Commerce antérieurs à ceux que vous avez installés. Procédez comme suit :

1. Dans le précédent [example](#issue), le package installé magento/sample-data version 0.74.0-beta15 ne peut pas être mis à niveau vers la version 1.0.0-beta. Cependant, 0.74.0-beta15 peut être mis à niveau vers 0.74.0-beta16 (ou d’autres). Modifier `composer.json` pour effectuer l’une de ces modifications. En règle générale, les versions demandées par votre projet sont définies dans la variable `require` ou `require-dev` de l’objet de ce fichier JSON. Selon les options des versions de package fournies, elles peuvent spécifier une version spécifique ou une contrainte. Pour obtenir des instructions générales sur l’utilisation du compositeur, si vous utilisez notre infrastructure cloud, reportez-vous à la section [Cloud pour Adobe Commerce > Technologies et exigences > Compositeur](https://devdocs.magento.com/cloud/reference/cloud-composer.html#files) dans notre documentation destinée aux développeurs. Si vous utilisez Adobe Commerce sur site, reportez-vous à la section [Adobe Commerce > Guide d’installation > Installer Adobe Commerce à l’aide du compositeur](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) .
1. Maintenant, essayez le contrôle de préparation. Réviser [Présentation de la mise à niveau d’Adobe Commerce > Exécuter le gestionnaire de modules > Contrôle de l’état de préparation de l’étape 1](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-readiness.html) dans notre documentation destinée aux développeurs.
1. Si la vérification de l’état de préparation échoue avec un autre message d’échec de vérification de dépendance des composants, cliquez sur les liens suivants selon que vous utilisez ou non [Adobe Commerce](#magento-commerce-magento-commerce-cloud) ou [Magento Open Source](#opensource) pour obtenir d’autres étapes de dépannage.

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. Contactez le développeur de l’extension pour qu’il vous aide. Vous trouverez leurs coordonnées sur la page à partir de laquelle vous avez acheté l’extension sur le Commerce Marketplace. Recherchez le **Contacter le vendeur** dans le panneau de droite. Tous les développeurs Commerce doivent fournir un guide d’installation et d’utilisateur lorsqu’ils publient une extension sur Marketplace. Vous trouverez les deux sur le côté droit de leur landing page.
1. Si vous ne recevez pas de réponse du vendeur dans un délai raisonnable, veuillez [contactez l’assistance Marketplace](mailto:commercemarketplacesupport@adobe.com) afin que nous puissions leur rappeler leurs engagements d’assistance clientèle.

## Magento Open Source {#opensource}

Demande d’assistance à l’adresse [notre forum principal](https://community.magento.com/) ou [contacter un partenaire Adobe Commerce ;](https://magento.com/find-a-partner) qui aide à résoudre les problèmes d’Open Source.
