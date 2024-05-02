---
title: Aide générale de dépannage des modules personnalisés
description: Cet article présente les outils généraux permettant de résoudre les problèmes liés aux modules personnalisés dans Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Aide générale de dépannage des modules personnalisés

Cet article présente les outils généraux permettant de résoudre les problèmes liés aux modules personnalisés dans Adobe Commerce.

## Problème

Si vous vous rendez compte qu’il existe un problème avec les fonctionnalités de votre module personnalisé et que vous n’obtenez aucun message d’erreur évident indiquant le problème, vous souhaiterez consulter les journaux de votre instance.

## Solution

Vérifiez les journaux pour voir s’il existe des entrées avec le nom du module personnalisé dans l’erreur.  Selon les erreurs impliquées, la solution peut se présenter ou vous devrez peut-être inclure vos informations utiles dans le journal Adobe Commerce si vous souhaitez ouvrir une [Ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Consultez les paragraphes suivants pour obtenir des informations sur l’emplacement des journaux et les solutions possibles.

### Adobe Commerce (toutes les méthodes de déploiement), Magento Open Source, toutes les versions 2.X

1. Emplacements des journaux :
   * [Journaux d’architecture du plan de démarrage pour l’infrastructure cloud d’Adobe Commerce](/help/how-to/general/log-locations-directories-for-starter-plan.md) dans notre base de connaissances de soutien.
   * [Journaux de planification de l’architecture d’Adobe Commerce sur l’infrastructure cloud Pro](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) dans notre base de connaissances de soutien.
1. En fonction des erreurs que vous trouvez, si vous souhaitez activer, désactiver ou désinstaller un module personnalisé, ces articles détaillent ces actions :
   * [Activation ou désactivation des modules](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-enable.html) dans notre documentation destinée aux développeurs.
   * [Désinstallation des modules](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall-mods.html) dans notre documentation destinée aux développeurs.

### Adobe Commerce sur l’infrastructure cloud, toutes les versions

1. Emplacements des journaux : [Adobe Commerce sur les journaux d’infrastructure cloud](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) dans notre documentation destinée aux développeurs.
1. En fonction des erreurs que vous constatez, si vous souhaitez activer, désactiver ou désinstaller un module personnalisé, ces articles de notre documentation destinée aux développeurs détaillent ces actions :
   * [Installation, gestion et mise à niveau des extensions](https://devdocs.magento.com/guides/v2.3/cloud/howtos/install-components.html).
   * [Échec du déploiement des composants](https://devdocs.magento.com/guides/v2.3/cloud/trouble/trouble_comp-deploy-fail.html).

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [Présentation des modules](https://devdocs.magento.com/guides/v2.3/architecture/archi_perspectives/components/modules/mod_intro.html)
* [Erreurs d’installation des exemples de données facultatifs](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_sample-data.html)
* [Gestion des exceptions](https://devdocs.magento.com/guides/v2.3/graphql/develop/exceptions.html)
* [Exceptions lors de l’installation](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_exceptions.html)
* [Exécution du gestionnaire de modules](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-checklist.html)
* [Fichiers de configuration de module](https://devdocs.magento.com/guides/v2.3/config-guide/config/config-files.html)
* [Erreurs de mémoire insuffisante](https://devdocs.magento.com/guides/v2.3/comp-mgr/trouble/cman/out-of-memory.html)
