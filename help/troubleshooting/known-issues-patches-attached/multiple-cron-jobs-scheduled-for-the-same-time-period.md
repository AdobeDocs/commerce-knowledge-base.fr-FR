---
title: Plusieurs tâches cron planifiées pour la même période
description: Cet article fournit un correctif pour un problème connu d’Adobe Commerce 2.2.2 lié au fait que plusieurs tâches cron soient planifiées pour s’exécuter en même temps après la modification des variables de certaines tâches dans l’administrateur Commerce.
exl-id: a3c1fe77-ed4c-43b5-8d6f-e5c549096c73
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Plusieurs tâches cron planifiées pour la même période

Cet article fournit un correctif pour un problème connu d’Adobe Commerce 2.2.2 lié au fait que plusieurs tâches cron soient planifiées pour s’exécuter en même temps après la modification des variables de certaines tâches dans l’administrateur Commerce.

## Problème

Lorsque cron est configuré pour s’exécuter toutes les minutes, si vous modifiez les variables temporelles de trois tâches planifiées dans Admin, le tableau de base de données `cron_schedule` présente des groupes de tâches multiples planifiées pour s’exécuter simultanément.

<u>Étapes à reproduire</u> :

1. Dans Commerce Admin, accédez à **Magasins** > Paramètres > **Configuration** > **AVANCÉ** > **Système** > **Cron (tâches planifiées)** > **Options de configuration Cron pour le groupe : par défaut.**
1. Configurez les options suivantes :
   * **Nettoyage de l’historique tous les** : désactivez la case à cocher **Utiliser le système**, puis définissez sur *1440*.
   * **Durée de vie de l’historique de succès** : décochez la case **Utiliser le système**, puis définissez sur *1440*.
   * **Durée de vie de l’historique des échecs** : décochez la case **Utiliser le système**, puis définissez sur *1440*.

1. Cliquez sur **Enregistrer la configuration**.
1. Dans SSH, exécutez la commande `crontab -e`.
1. Définissez cron pour qu’il s’exécute toutes les minutes.
1. Ouvrez trois onglets/fenêtres de terminal.
1. Accédez au répertoire Adobe Commerce `root/base/project` dans chaque fenêtre de terminal.
1. Exécutez la commande suivante dans chaque onglet/fenêtre :

   ```bash
   bin/magento cache:flush && bin/magento cron:run && bin/magento cache:flush && bin/magento cron:run
   ```

1. Accédez à MySQL et exécutez la requête suivante :

   ```sql
   SELECT job_code, scheduled_at, count as count FROM cron_schedule GROUP BY job_code, scheduled_at HAVING count > 1 ORDER BY scheduled_at;
   ```

1. Voir les groupes de tâches planifiées pour s’exécuter en même temps.

<u>Résultat attendu</u> : un cron `job_code` doit être planifié pour une période donnée.

<u>Résultat réel</u> : plusieurs tâches cron sont planifiées pour la même période.

## Solution

Pour Adobe Commerce sur les commerçants d’infrastructure de cloud, [la mise à jour des outils de la CEE](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) résoudra le problème.

Les commerçants sur site d’Adobe Commerce doivent appliquer l’un des correctifs ci-joint pour résoudre le problème.

## Correctifs

Les correctifs sont joints à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur l’un des liens suivants :

* [Téléchargez MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch.](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip)
* [Téléchargez MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch.](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip)
* [Téléchargez MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch.](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* [Téléchargez MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch.](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip)
* [Téléchargez MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch.](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip)
* [Téléchargez MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch.](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip)
* [Téléchargez MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch.](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip)

### Versions Adobe Commerce compatibles

Les correctifs ont été créés pour une version spécifique indiquée dans le nom du fichier de correctif. Par exemple, MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch a été créé pour Adobe Commerce 2.2.4 et est le meilleur correctif à utiliser pour cette version.

Les correctifs sont également compatibles avec les versions suivantes :

* Pour Adobe Commerce on-premise 2.1.0-2.1.4 : [Télécharger MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip) Le correctif est également compatible (mais ne peut pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :
   * Adobe Commerce sur l’infrastructure cloud 2.1.0-2.1.4
* Pour Adobe Commerce On-Premise 2.1.5-2.1.12 : [Télécharger MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip) Le correctif est également compatible (mais ne peut pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :
   * Adobe Commerce sur l’infrastructure cloud 2.1.5-2.1.12
* Pour Adobe Commerce sur l’infrastructure cloud 2.1.13 : [Téléchargez MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* Pour Adobe Commerce On-Premise 2.1.14-2.1.17 : [Télécharger MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip) Le correctif est également compatible (mais ne peut pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :
   * Adobe Commerce On-Premise 2.1.18
   * Adobe Commerce sur l’infrastructure cloud 2.1.14-2.1.18
* Pour Adobe Commerce on-premise 2.2.0-2.2.1 : [Télécharger MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip) Le correctif est également compatible (mais ne peut pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :
   * Adobe Commerce sur l’infrastructure cloud 2.2.0-2.2.1
* Pour Adobe Commerce On-Premise 2.2.0-2.2.3 : [Télécharger MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip) Le correctif est également compatible (mais ne peut pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :
   * Adobe Commerce sur l’infrastructure cloud 2.2.0-2.2.3
* Pour Adobe Commerce On-Premise 2.2.4 : [Télécharger MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip) Le correctif est également compatible (mais ne résout pas le problème) avec les versions et éditions Adobe Commerce suivantes :
   * Adobe Commerce sur l’infrastructure cloud 2.2.4

## Comment appliquer le correctif

Pour obtenir des instructions, reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.

## Fichiers attachés
