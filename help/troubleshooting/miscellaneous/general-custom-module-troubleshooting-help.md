---
title: Aide générale à la résolution des problèmes liés aux modules personnalisés
description: Cet article présente des outils généraux pour vous aider à résoudre les problèmes liés aux modules personnalisés dans Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Aide générale à la résolution des problèmes liés aux modules personnalisés

Cet article présente des outils généraux pour vous aider à résoudre les problèmes liés aux modules personnalisés dans Adobe Commerce.

## Problème

Si vous constatez qu’il existe un problème avec les fonctionnalités de votre module personnalisé et que vous n’obtenez aucun message d’erreur évident signalant le problème, vous souhaiterez consulter les journaux de votre instance.

## Solution

Vérifiez les journaux pour voir s’il y a des entrées avec le nom du module personnalisé dans l’erreur.  Selon les erreurs rencontrées, la solution peut se présenter ou vous devrez peut-être inclure vos informations utiles dans le journal Adobe Commerce si vous souhaitez ouvrir un ticket d’assistance [&#128279;](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket). Consultez les paragraphes suivants pour plus d’informations sur l’emplacement des journaux et les solutions possibles.

### Adobe Commerce (toutes les méthodes de déploiement), Magento Open Source, toutes les versions 2.X

1. L’emplacement des journaux est placé dans [Adobe Commerce sur l’infrastructure cloud. Consultez les journaux d’architecture Pro plan](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) dans notre base de connaissances d’assistance.
1. En fonction des erreurs détectées, si vous souhaitez activer, désactiver ou désinstaller un module personnalisé, ces articles détaillent ces actions :
   * [Activez ou désactivez les modules](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/manage-modules) dans notre documentation destinée aux développeurs.
   * [Désinstallez les modules](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules) dans notre documentation destinée aux développeurs.

### Adobe Commerce sur les infrastructures cloud, toutes versions confondues

1. Emplacements des journaux : [journaux d’Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) dans notre documentation destinée aux développeurs.
1. En fonction des erreurs détectées, si vous souhaitez activer, désactiver ou désinstaller un module personnalisé, ces articles de notre documentation destinée aux développeurs détaillent ces actions :
   * [Installation, gestion et mise à niveau des extensions](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions).
   * [Échec du déploiement des composants](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment).

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [Présentation du module](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [Erreurs lors de l’installation des données d’exemple facultatives](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/errors-installing-optional-sample-data)
* [Gestion des exceptions](https://developer.adobe.com/commerce/webapi/graphql/develop/exceptions/)
* [Exceptions lors de l’installation](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/exceptions-during-installation)
* [Exécutez le gestionnaire de modules](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites)
* [Fichiers de configuration du module](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/module-files)
* [Erreurs de mémoire insuffisante](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)
