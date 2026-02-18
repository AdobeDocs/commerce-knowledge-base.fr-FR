---
title: '[!DNL Cron] tâches verrouillent les tâches d''autres groupes'
description: Cet article fournit une solution au problème d’infrastructure cloud d’Adobe Commerce relatif à certaines tâches  [!DNL cron]  long terme bloquant d’autres  [!DNL cron] .
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# [!DNL Cron] tâches verrouillent les tâches d&#39;autres groupes

Cet article fournit une solution au problème d’infrastructure cloud d’Adobe Commerce relatif à certaines tâches [!DNL cron] de longue durée qui bloquent d’autres tâches [!DNL cron].

## Produits et versions concernés

* Architecture de plan Pro d’Adobe Commerce sur les infrastructures cloud
* Intégration avant mai 2019

## Problème

Sur Adobe Commerce pour le cloud, lorsque vous avez des tâches [!DNL cron] complexes (tâches de longue durée), elles peuvent verrouiller d’autres tâches pour exécution. Par exemple, la tâche des indexeurs réindexe les indexeurs invalidés. Son exécution peut prendre quelques heures. Elle verrouille également d’autres tâches de [!DNL cron] par défaut telles que l’envoi d’e-mails, la génération de plans de site, les notifications client et d’autres tâches personnalisées.

<u>Symptômes</u> :

Les processus exécutés par les traitements [!DNL cron] ne sont pas exécutés. Par exemple, les mises à jour des produits ne sont pas appliquées pendant les heures ou les clients signalent ne pas recevoir d’e-mails.

Lorsque vous ouvrez la table de base de données `cron_schedule`, vous voyez les tâches avec le statut `missed`.

## Cause

Auparavant, dans notre environnement cloud, le serveur Jenkins était utilisé pour exécuter des tâches [!DNL cron]. Jenkins n’exécutera qu’une seule instance d’une tâche à la fois. Par conséquent, un seul processus `bin/magento cron:run` sera exécuté à la fois.

## Solution

1. Contactez l’[assistance Adobe Commerce](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) pour activer les [!DNL crons] autogérés.
1. Modifiez le fichier `.magento.app.yaml` dans le répertoire racine du code pour Adobe Commerce dans la branche [!DNL Git]. Ajoutez le code suivant :

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Enregistrez le fichier et envoyez les mises à jour aux environnements d’évaluation et de production (de la même manière que pour les environnements d’intégration).

>[!NOTE]
>
>Il n’est pas nécessaire de transférer les anciennes configurations de [!DNL cron] comportant plusieurs `cron:run` vers le nouveau planning de [!DNL cron]. La tâche de `cron:run` standard, ajoutée comme décrit ci-dessus, est suffisante. Cependant, il est nécessaire de transférer vos tâches personnalisées si vous en aviez.

### Vérifiez si les [!DNL cron] autogérés sont activés (uniquement pour l’évaluation et la production Cloud Pro).

Pour vérifier si le [!DNL cron] autogéré est activé, exécutez la commande `crontab -l` et observez le résultat :

* Les [!DNL cron] auto-gérés sont activés si vous pouvez voir les tâches, comme dans l’exemple suivant :

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* Le [!DNL cron] autogéré n’est pas activé si vous ne parvenez pas à voir les tâches et à obtenir le message d’erreur *vous n’êtes pas autorisé à utiliser ce programme »*

>[!NOTE]
>
>La commande mentionnée ci-dessus pour vérifier si le [!DNL cron] autogéré est activé ne s’applique pas à un plan de démarrage et dans l’environnement de développement/intégration.

## Lecture connexe

* [Configurer [!DNL cron] tâches](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) dans notre documentation destinée aux développeurs
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
