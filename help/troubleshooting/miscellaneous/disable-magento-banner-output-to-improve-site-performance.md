---
title: Désactivez la sortie Adobe Commerce Banner pour améliorer les performances du site.
description: Cet article fournit un correctif pour les performances faibles du site. Les faibles performances du site peuvent être dues à l’activation mais à la non-utilisation du module « Magento_Banner ». La désactivation de la sortie du module peut améliorer les performances du site. Consultez l’article pour connaître les étapes de résolution.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 76ef59dc37504f50d55734a90c9ce5b30bb83175
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Désactivez la sortie Adobe Commerce Banner pour améliorer les performances du site.

Cet article fournit un correctif pour les performances faibles du site. Les faibles performances du site peuvent être dues à l’activation du module `Magento_Banner`, mais à sa non-utilisation. La désactivation de la sortie du module peut améliorer les performances du site. Consultez l’article pour connaître les étapes de résolution.

>[!NOTE]
>
>Si vous utilisez la fonctionnalité Bannière Adobe Commerce, reportez-vous à l’article [Les requêtes AJAX à débit élevé entraînent des performances médiocres](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) de notre base de connaissances du support pour obtenir des recommandations sur la manière d’éviter les problèmes de performances causés par des requêtes Ajax excessives.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud v.2.x.x
* Adobe Commerce on-premise v.2.2.x et 2.3.x

## Problème

Le module `Magento_Banner` est activé, mais pas utilisé.

Pour vérifier si c’est le cas :

Pour Adobe Commerce sur l’infrastructure cloud 2.2.x :

1. Connectez-vous à l’administration Commerce.
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Banners]**.
1. Si la grille affichée sur cette page est vide, vous ne disposez d’aucune bannière.

Si vous ne voyez pas l’option **[!UICONTROL Banners]** sous **[!UICONTROL Content]** > **[!UICONTROL Elements]**, cela signifie que vous avez déjà appliqué les recommandations de cet article.

Pour Adobe Commerce sur les infrastructures cloud 2.3.x et ultérieures (la fonctionnalité a été [renommée dans la version 2.3.x](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)) :

1. Connectez-vous à l’administration Commerce.
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Dynamic Blocks]**.
1. Si la grille affichée sur cette page est vide, vous n’avez pas de blocs dynamiques (bannières).

Si vous ne voyez pas l’option **[!UICONTROL Dynamic Blocks]** sous **[!UICONTROL Content]** > **[!UICONTROL Elements]**, cela signifie que vous avez déjà appliqué la recommandation de cet article. Pour afficher à nouveau l’option Bannières, annulez le processus.

## Cause

Lorsque le module `Magento_Banner` est activé, Adobe Commerce envoie des requêtes Ajax du storefront au serveur pour obtenir les informations de bannière. Ces requêtes Ajax ont un impact sur les performances, en particulier dans des conditions de forte charge (volume élevé et trafic élevé). Si la fonctionnalité n’est pas utilisée, il est recommandé de désactiver la sortie du module. Il n’est pas recommandé de désactiver le module en raison de problèmes de dépendance.

## Solution

>[!WARNING]
>
>Nous vous recommandons vivement de tester les modifications sur l’[environnement d’évaluation/d’intégration](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) avant de l’appliquer à la production. Nous vous recommandons également de disposer d’une sauvegarde récente avant toute manipulation.

1. Désactivez la sortie du module `Magento_Banner`, comme décrit dans la section [Désactiver la sortie du module](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/disable-module-output) dans notre documentation destinée aux développeurs. Le nom du module que vous devez utiliser est `Magento_Banner`.
1. Déployez votre code. Pour Adobe Commerce sur les infrastructures cloud, procédez au déploiement comme décrit dans l’article [Déployer votre boutique](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) de notre documentation destinée aux développeurs.
1. Après avoir désactivé la sortie du module, le menu n’apparaît plus dans l’interface d’administration.
1. Vous ne verrez plus l’option Bannière ou Dynamique sous **[!UICONTROL Content]** > **[!UICONTROL Elements]**. Pour afficher à nouveau les options, [activez la sortie du module](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/disable-module-output?lang=en#disable-module-output-in-a-simple-deployment).

