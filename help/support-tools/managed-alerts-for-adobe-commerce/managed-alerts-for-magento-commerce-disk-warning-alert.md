---
title: "Alertes gérées pour Adobe Commerce : alerte d’avertissement sur le disque"
description: Cet article décrit les étapes de dépannage lors de la réception d’une alerte de disque d’avertissement pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.
exl-id: 07b34db1-11ec-4cf2-ae47-cfc067f91383
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: d7dcb23eee8793b6b97717827feb88c09994bd8b
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Alertes gérées pour Adobe Commerce : alerte d’avertissement sur le disque

Cet article décrit les étapes de dépannage lors de la réception d’une alerte de disque d’avertissement pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.

![alerte d’avertissement de disque](assets/disk-warning-magento-managed.png){width="500"}

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, Formule pour l’architecture.

## Problème

Vous recevrez une alerte dans New Relic si vous avez signé jusqu’à [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) et qu’un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe pour fournir aux clients un ensemble standard utilisant les informations du service d’assistance et d’ingénierie.

<u> **Do!** </u>

* Abandonnez tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez votre site en mode de maintenance immédiatement si votre site est ou ne répond plus complètement. Pour les étapes, reportez-vous au [Guide d&#39;installation > Activer ou désactiver le mode de maintenance](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) dans notre documentation destinée aux développeurs. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées afin de vous assurer que vous pouvez toujours accéder à votre site pour la résolution des problèmes. Pour les étapes, reportez-vous à la section [Maintenance de la liste des adresses IP exemptées](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) dans notre documentation destinée aux développeurs.

<u> **Ne pas faire !** </u>

* Lancez d’autres campagnes marketing qui peuvent générer des pages vues supplémentaires sur votre site.
* Exécutez des indexeurs ou des crons supplémentaires qui peuvent entraîner une contrainte supplémentaire sur le processeur ou le disque.
* Effectuez toutes les tâches administratives importantes (c’est-à-dire l’administration de Commerce, les importations/exportations de données).
* Effacez le cache. Votre site peut ne plus être réactif (si vous n’êtes pas déjà en panne) si vous effectuez l’une des actions &quot;Ne pas&quot; avant d’avoir enquêté et résolu la cause de l’alerte.

## Solution

Pour identifier et résoudre le problème, procédez comme suit :

1. Dans New Relic, consultez les disques pour une utilisation optimale. Pour les étapes, reportez-vous à l’onglet Stockage de New Relic [Page Hôtes de surveillance de l’infrastructure](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) :
   * Si, dans New Relic, vous constatez une augmentation lente de l’utilisation du disque, essayez les options suivantes :
   * Optimisation de l’espace disque en ajustant l’allocation de l’espace. Pour les étapes, reportez-vous à la section [Gestion de l’espace disque](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) dans notre documentation destinée aux développeurs. Vous devrez peut-être également demander plus d’espace disque (contactez votre équipe de compte d’Adobe).
   * Effacez l’espace disque pour MySQL. Pour connaître les étapes, reportez-vous à la section [L’espace disque MySQL est faible](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) .
   * Si New Relic affiche une utilisation de disque en augmentation rapide, cela peut indiquer qu’un problème a provoqué une augmentation très rapide d’un fichier dans un répertoire. Effectuez les vérifications suivantes :
1. Vérifiez l&#39;espace disque global pour identifier le problème en exécutant la commande suivante dans l&#39;interface de ligne de commande/le terminal : `df -h`
1. Après avoir identifié un répertoire avec une utilisation de disque inattendue importante et croissante, vous devez vérifier le système de fichiers concerné. L’exemple suivant montre comment vérifier le répertoire de fichiers `pub/media/`. Il s’agit du répertoire utilisé par Adobe Commerce pour le stockage des journaux et des fichiers multimédias volumineux. Cependant, vous devez exécuter cette commande pour tout répertoire présentant une utilisation inattendue du disque : `du -sch ~/pub/media/*`.

Si la sortie du terminal affiche un fichier dans l’un de ces répertoires, ce qui augmente rapidement l’utilisation du disque et si vous savez que le contenu du fichier n’est pas nécessaire, envisagez de le supprimer. Si vous n’êtes pas à l’aise avec cette action, [soumettez un ticket d’assistance Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
