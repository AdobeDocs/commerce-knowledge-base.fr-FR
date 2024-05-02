---
title: Problèmes de performances provoqués par les requêtes Ajax excessives
description: Cet article fournit un correctif pour le problème de performances connu d’Adobe Commerce causé par des requêtes Ajax excessives. Le problème a été corrigé dans Adobe Commerce 2.3.4.
exl-id: d9a69406-3970-4556-aa6a-1309b24366d8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Problèmes de performances provoqués par les requêtes Ajax excessives

Cet article fournit un correctif pour le problème de performances connu d’Adobe Commerce causé par des requêtes Ajax excessives. Le problème a été corrigé dans Adobe Commerce 2.3.4.

## Problème

Adobe Commerce peut envoyer des messages redondants [Requêtes Ajax](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) de storefront au serveur pour obtenir les informations sur la bannière et les informations sur les clients. Ces requêtes Ajax ont un impact sur les performances, en particulier dans les conditions de charge élevée (volume élevé et trafic élevé). Ainsi, si la fonctionnalité de bannière n’est pas utilisée, il est recommandé de [Désactivation de la sortie du module Adobe Commerce Banner](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md) et appliquez le correctif pour améliorer la récupération des informations sur les clients.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier ou cliquez sur le lien suivant :

[Téléchargez le MDVA-24597\_EE\_2.2.9\_COMPOSER\_v1.patch.](assets/MDVA-24597_EE_2.2.9_COMPOSER_v1.patch.zip)

### Versions Adobe Commerce compatibles

Le correctif est valide pour les produits et versions suivants :

* Adobe Commerce sur l’infrastructure cloud 2.2.9
* Adobe Commerce on-premise 2.2.9

Si vous disposez d’une version différente d’Adobe Commerce, envisagez d’effectuer une mise à jour vers la dernière version 2.3.x. S’il ne s’agit pas d’une option actuellement, veuillez [contacter l’assistance d’Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) et demandez un correctif pour votre version.

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
