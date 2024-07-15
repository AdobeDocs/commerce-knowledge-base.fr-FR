---
title: Les tâches de blocage verrouillent les tâches d’autres groupes.
description: Cet article fournit une solution à Adobe Commerce concernant les problèmes d’infrastructure de cloud liés à certaines tâches cron à long terme qui bloquent d’autres tâches cron.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: faa80e8233438fc15781341b3a9d5325269d6d20
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Les tâches de blocage verrouillent les tâches d’autres groupes.

Cet article fournit une solution à Adobe Commerce concernant les problèmes d’infrastructure de cloud liés à certaines tâches cron à long terme qui bloquent d’autres tâches cron.

## Produits et versions concernés

* Architecture de plan d’Adobe Commerce sur l’infrastructure cloud Pro
* embarqué avant mai 2019

## Problème

Dans Adobe Commerce pour le cloud, lorsque vous avez des tâches cron complexes (tâches à long terme), elles peuvent verrouiller d’autres tâches pour exécution. Par exemple, la tâche des indexeurs reindexe les indexeurs invalidés. Cela peut prendre quelques heures et verrouiller d’autres tâches cron par défaut, comme envoyer des emails, générer des plans de site, des notifications client et d’autres tâches personnalisées.

<u>Symptômes</u> :

Les traitements exécutés par les traitements cron ne sont pas effectués. Par exemple, les mises à jour de produit ne sont pas appliquées pendant des heures ou les clients signalent qu’ils ne reçoivent pas d’emails.

Lorsque vous ouvrez la table de base de données `cron_schedule`, les tâches avec l’état `missed` s’affichent.

## Cause

Auparavant, dans notre environnement cloud, le serveur Jenkins était utilisé pour exécuter les tâches cron. Jenkins n’exécute qu’une seule instance d’une tâche à la fois. Par conséquent, un seul processus `bin/magento cron:run` s’exécute à la fois.

## Solution

1. Contactez le [support Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour activer les fils auto-gérés.
1. Modifiez le fichier `.magento.app.yaml` dans le répertoire racine du code pour Adobe Commerce dans la branche Git. Ajoutez ce qui suit :

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Enregistrez le fichier et publiez les mises à jour dans les environnements d’évaluation et de production (comme vous le faites pour les environnements d’intégration).

>[!NOTE]
>
>Il n’est pas nécessaire de transférer d’anciennes configurations cron où plusieurs `cron:run` sont présents dans le nouveau planning cron ; la tâche `cron:run` régulière, ajoutée comme décrit ci-dessus, suffit. Cependant, il est nécessaire de transférer vos tâches personnalisées si vous en aviez.

### Vérifiez si le cron auto-géré est activé (uniquement pour l’évaluation et la production de Cloud Pro).

Pour vérifier si le cron auto-géré est activé, exécutez la commande `crontab -l` et observez le résultat :

* La fonction cron auto-géré est activée si vous pouvez afficher les tâches comme suit :

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* Le cron auto-géré n’est pas activé si vous ne pouvez pas voir les tâches et obtenir le message d’erreur *&quot;vous n’êtes pas autorisé à utiliser ce programme&quot;*.

>[!NOTE]
>
>La commande mentionnée ci-dessus pour vérifier si le cron auto-géré est activé ne s’applique pas à un plan de démarrage et à l’environnement de développement/intégration.

## Lecture connexe

* [Configurez les tâches cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) dans notre documentation destinée aux développeurs.
