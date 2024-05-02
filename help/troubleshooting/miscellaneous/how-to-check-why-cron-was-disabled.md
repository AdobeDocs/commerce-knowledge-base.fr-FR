---
title: Comment vérifier pourquoi [!DNL cron] a été désactivé
description: Cet article propose des solutions de dépannage pour les problèmes liés à cron dans Adobe Commerce sur les produits d’infrastructure cloud.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Comment vérifier pourquoi [!DNL cron] a été désactivé

Cet article propose des solutions de dépannage pour les problèmes liés à [!DNL cron] dans Adobe Commerce sur les produits d’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions

## Problème

## Voici les symptômes de [!DNL cron] Problèmes :

Vous avez remarqué que votre [!DNL cron] ne courait pas.
Par exemple, les lignes suivantes s’affichent dans la variable `app/etc/env.php` fichier :

```'cron' =>
  array (
    'enabled' => 0
  ),
```

Un tableau vide signifie que la variable [!DNL cron] is **enabled**:

```'cron' =>
  array (
  ),
```

## Causes

Plusieurs raisons peuvent expliquer que la variable [!DNL cron] n’est actuellement pas actif :

1. La variable [!DNL cron] a été désactivé en raison d’une absence [!DNL OpCache] paramètres.
1. L’équipe d’infrastructure a désactivé votre [!DNL cron], car cela provoquait des performances médiocres/une diminution des performances de votre site.
1. La variable [!DNL cron] n’a pas été réactivé, car votre déploiement a échoué.

Consultez l’une des sections suivantes pour une solution à votre problème.

## Solutions

### Solution à défaut [!DNL OpCache] paramètres {#solution-missed-opcache-settings}

Voir [[!DNL Cron] arrêté en raison d’une configuration incorrecte ou d’une absence [!DNL OpCache] paramètres](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) dans notre base de connaissances Commerce.

### Solution pour les personnes handicapées par l’équipe d’infrastructure {#solution-disabled-by-infrastructure-team}

1. Vérifiez vos précédents tickets d’assistance pour lesquels votre site était en panne ou ne répondait pas.
1. Vérifiez ensuite si l’équipe d’infrastructure a indiqué qu’elle l’avait désactivé.
1. Vérifiez que vous avez résolu les problèmes/préoccupations soulevés par l’équipe d’infrastructure.
1. Envoyer un [Demande d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) si vous avez besoin d’aide supplémentaire pour demander la réactivation de la variable [!DNL cron] et expliquer comment vous avez résolu les problèmes que l&#39;équipe chargée de l&#39;infrastructure a indiqués.

### Solution pour le déploiement en échec {#solution-deployment-failed}

Consultez les journaux de déploiement :

* [Affichage et gestion des journaux](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) dans notre guide Commerce on Cloud Infrastructure.
* [Vérification du journal de déploiement si l’interface utilisateur de Cloud comporte *`log snipped`* error](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) dans notre base de connaissances Commerce.

1. Si le déploiement a échoué pendant la `setup:upgrade` , l’étape [!DNL cron] n’a pas été réactivé.
Par exemple : cette ligne s’affiche dans le journal de déploiement :

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. Sinon, le déploiement aurait échoué à une autre étape. Vérifiez le journal de déploiement et assurez-vous que les deux lignes apparaissent (exemple ci-dessous). Si vous ne voyez pas les deux lignes similaires à celle-ci dans le journal, cela signifie que la variable [!DNL cron] n’a pas été réactivé :

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
..<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**Envoyer un [Demande d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) si vous avez besoin d’aide supplémentaire.**
