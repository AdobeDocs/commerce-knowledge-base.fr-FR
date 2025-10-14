---
title: Les tâches '[!DNL Cron] verrouillent les tâches d’autres groupes'
description: Cet article fournit une solution à Adobe Commerce pour le problème d’infrastructure cloud lié à certaines tâches  [!DNL cron] à long terme qui bloquent d’autres tâches [!DNL cron] .
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# [!DNL Cron] tâches verrouillent les tâches d’autres groupes

Cet article fournit une solution à Adobe Commerce pour le problème d’infrastructure cloud lié à certaines tâches [!DNL cron] à long terme qui bloquent d’autres tâches [!DNL cron].

## Produits et versions concernés

* Architecture de plan d’Adobe Commerce sur l’infrastructure cloud Pro
* embarqué avant mai 2019

## Problème

Dans Adobe Commerce pour le cloud, lorsque vous avez des tâches [!DNL cron] complexes (tâches à long terme), elles peuvent verrouiller d’autres tâches pour exécution. Par exemple, la tâche des indexeurs reindexe les indexeurs invalidés. Cela peut prendre quelques heures et verrouiller d’autres tâches par défaut, telles que l’envoi d’emails, la génération de plans de site, de notifications client et d’autres tâches personnalisées.[!DNL cron]

<u>Symptômes</u> :

Les processus exécutés par les tâches [!DNL cron] ne sont pas effectués. Par exemple, les mises à jour de produit ne sont pas appliquées pendant des heures ou les clients signalent qu’ils ne reçoivent pas d’emails.

Lorsque vous ouvrez la table de base de données `cron_schedule`, les tâches avec l’état `missed` s’affichent.

## Cause

Auparavant, dans notre environnement cloud, le serveur Jenkins était utilisé pour exécuter [!DNL cron] tâches. Jenkins n’exécute qu’une seule instance d’une tâche à la fois. Par conséquent, un seul processus `bin/magento cron:run` s’exécute à la fois.

## Solution

1. Contactez le [support Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour que [!DNL crons] auto-géré soit activé.
1. Modifiez le fichier `.magento.app.yaml` dans le répertoire racine du code pour Adobe Commerce dans la branche [!DNL Git]. Ajoutez ce qui suit :

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Enregistrez le fichier et publiez les mises à jour dans les environnements d’évaluation et de production (comme vous le faites pour les environnements d’intégration).

>[!NOTE]
>
>Il n&#39;est pas nécessaire de transférer d&#39;anciennes configurations [!DNL cron] où plusieurs `cron:run` sont présents dans le nouveau planning [!DNL cron] ; la tâche `cron:run` régulière, ajoutée comme décrit ci-dessus, suffit. Cependant, il est nécessaire de transférer vos tâches personnalisées si vous en aviez.

### Vérifiez si le [!DNL cron] autogéré est activé (uniquement pour l’évaluation et la production de Cloud Pro).

Pour vérifier si le [!DNL cron] autogéré est activé, exécutez la commande `crontab -l` et observez le résultat :

* La fonction [!DNL cron] auto-gérée est activée si vous pouvez afficher les tâches comme suit :

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* L&#39;auto-géré [!DNL cron] n&#39;est pas activé si vous ne pouvez pas voir les tâches et obtenir le message d&#39;erreur *&quot;vous n&#39;êtes pas autorisé à utiliser ce programme&quot;*.

>[!NOTE]
>
>La commande mentionnée ci-dessus pour vérifier si l&#39;auto-gestion [!DNL cron] est activée ne s&#39;applique pas à un plan de démarrage et à l&#39;environnement de développement/intégration.

## Lecture connexe

* [Configuration de [!DNL cron] tâches](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) dans notre documentation destinée aux développeurs
* [&#x200B; Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
