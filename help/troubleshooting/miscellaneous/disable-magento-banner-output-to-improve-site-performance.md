---
title: Désactiver la sortie de la bannière Adobe Commerce pour améliorer les performances du site
description: Cet article fournit un correctif pour les faibles performances du site. Les faibles performances du site peuvent être dues à l’activation du module "Magento_Banner", mais pas à son utilisation. La désactivation de la sortie du module peut améliorer les performances du site. Consultez l’article pour connaître les étapes de résolution.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Désactiver la sortie de la bannière Adobe Commerce pour améliorer les performances du site

Cet article fournit un correctif pour les faibles performances du site. Les faibles performances du site peuvent être dues à l’activation du module `Magento_Banner`, mais pas à son utilisation. La désactivation de la sortie du module peut améliorer les performances du site. Consultez l’article pour connaître les étapes de résolution.

>[!NOTE]
>
>Si vous utilisez la fonctionnalité de bannière Adobe Commerce, reportez-vous à l’article [Les demandes d’AJAX à débit élevé provoquent des performances médiocres](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) de notre base de connaissances de support pour obtenir des recommandations sur la manière d’éviter les problèmes de performances causés par des demandes Ajax excessives.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud v.2.x.x
* Adobe Commerce On-Premise v.2.2.x et 2.3.x

## Problème

Le module `Magento_Banner` est activé, mais n’est pas utilisé.

Pour vérifier si c’est le cas :

Pour Adobe Commerce sur l’infrastructure cloud 2.2.x :

1. Connectez-vous à l’administrateur Commerce.
1. Accédez à **Contenu** > *Éléments* > **Bannières**.
1. Si la grille affichée sur cette page est vide, vous ne disposez d’aucune bannière.

Si vous ne voyez pas l’option **Bannières** sous **Contenu** > *Éléments*, ce n’est pas le cas et les recommandations de cet article ne peuvent pas être appliquées.

Pour Adobe Commerce sur l’infrastructure cloud 2.3.x (la fonctionnalité a été [ renommée en v 2.3.x](https://devdocs.magento.com/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)) :

1. Connectez-vous à l’administrateur Commerce.
1. Accédez à **Contenu** > *Éléments >* **Blocs dynamiques**.
1. Si la grille affichée sur cette page est vide, vous ne disposez d’aucun bloc dynamique (bannières).

Si vous ne voyez pas l’option **Blocs dynamiques** sous **Contenu** > *Éléments*, ce n’est pas le cas et les recommandations de cet article ne peuvent pas être appliquées.

## Cause

Lorsque le module `Magento_Banner` est activé, Adobe Commerce envoie les demandes Ajax depuis le storefront au serveur pour obtenir les informations sur la bannière. Ces requêtes Ajax ont un impact sur les performances, en particulier dans les conditions de charge élevée (volume élevé et trafic élevé). Si la fonctionnalité n’est pas utilisée, il est recommandé de désactiver la sortie du module. Il n’est pas recommandé de désactiver le module en raison des problèmes de dépendance.

## Solution

>[!WARNING]
>
>Nous vous recommandons vivement de tester les modifications dans l’ [environnement d’évaluation/d’intégration](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) avant de les appliquer à la production. Nous vous recommandons également d’effectuer une sauvegarde récente avant toute manipulation.

1. Désactivez la sortie du module `Magento_Banner`, comme décrit dans la section [Désactiver la sortie du module](https://devdocs.magento.com/guides/v2.3/config-guide/config/disable-module-output.html) de notre documentation destinée aux développeurs. Le nom du module que vous devez utiliser est `Magento_Banner`.
1. Déployez votre code. Pour Adobe Commerce sur l’infrastructure cloud, déployez comme décrit dans l’article [Déployez votre boutique](https://devdocs.magento.com/guides/v2.3/cloud/live/stage-prod-live.html) de notre documentation destinée aux développeurs.
