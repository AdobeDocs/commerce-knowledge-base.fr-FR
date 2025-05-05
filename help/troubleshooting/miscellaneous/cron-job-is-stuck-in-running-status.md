---
title: La tâche "[!DNL Cron] est bloquée dans l’état **running**"
description: Cet article fournit des solutions lorsque les tâches Adobe Commerce [!DNL cron] ne se terminent pas et persistent dans un état "en cours d’exécution", ce qui empêche l’exécution d’autres tâches  [!DNL cron] de s’exécuter. Cela peut se produire pour plusieurs raisons, telles que des problèmes réseau, des blocages d’application, des problèmes de redéploiement.
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# La tâche [!DNL Cron] est bloquée dans l’état &quot;en cours&quot;

Cet article fournit des solutions pour les tâches Adobe Commerce [!DNL cron] dont l’exécution n’est pas terminée et qui restent dans un état &quot;en cours d’exécution&quot;, ce qui empêche les autres tâches [!DNL cron] de s’exécuter. Cela peut se produire pour plusieurs raisons, telles que des problèmes réseau, des blocages d’application, des problèmes de redéploiement.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud, toutes les versions

## Symptôme {#symptom}

Les symptômes des tâches [!DNL cron] qui doivent être réinitialisées sont les suivants :

* Une grande quantité de tâches s’affiche dans la file d’attente `cron_schedule`
* Les performances du site commencent à diminuer
* Les tâches ne s’exécutent pas selon le calendrier

## Solutions {#solutions}

### Solution pour arrêter toutes les tâches [!DNL cron] à la fois {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>L’exécution de cette commande sans l’option `--job-code` réinitialise *toutes* [!DNL cron] tâches, y compris celles en cours d’exécution. Nous vous recommandons donc de ne l’utiliser que dans des cas exceptionnels, par exemple après avoir vérifié que toutes les [!DNL cron] tâches doivent être réinitialisées. Le redéploiement exécute cette commande par défaut pour réinitialiser les tâches [!DNL cron], de sorte qu’elles récupèrent correctement une fois l’environnement sauvegardé. Évitez d’utiliser cette solution lorsque les indexeurs sont en cours d’exécution.

Pour résoudre ce problème, vous devez réinitialiser la ou les tâches [!DNL cron] à l’aide de la commande `cron:unlock`. Cette commande modifie l’état de la tâche [!DNL cron] dans la base de données, mettant ainsi fin à la tâche pour permettre la poursuite d’autres tâches planifiées.

1. Ouvrez un terminal et utilisez vos [clés SSH](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/secure-connections) pour vous connecter à l’environnement concerné.
1. Obtenez les informations d’identification de la base de données MySQL :    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. Connectez-vous à la base de données à l’aide de `mysql` :    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. Sélectionnez la base de données `main` :    ```shell    use main    ```
1. Recherchez toutes les tâches [!DNL cron] en cours d’exécution :    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. Copiez le `job_code` de toute tâche s’exécutant plus longtemps que d’habitude.
1. Utilisez les ID de planification de l’étape précédente pour déverrouiller des tâches [!DNL cron] spécifiques :    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### Solution pour arrêter un seul [!DNL cron] {#solution-stop-a-single-cron}

1. Ouvrez un terminal et utilisez vos [clés SSH](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/secure-connections) pour vous connecter à l’environnement concerné.
1. Vérifiez les tâches longues en cours à l’aide de la commande suivante :

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. Dans la sortie, comme dans l’exemple de sortie ci-dessous, vous verrez la date actuelle et la liste des processus. La colonne `START` indique l’heure ou la date de début du processus :

   ```
   Wed May  8 22:41:31 UTC 2019
   USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
   root       590  0.0  0.0  27528  2768 ?        Ss   Jan15   0:49 /usr/sbin/cron -f
   bxc2qly+ 25855  0.0  0.0  23724  2184 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe_stg-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe_stg-bxc2qlykqhbqe_stg
   bxc2qly+ 25860 57.7  1.3 584220 222692 ?       S    20:51   0:02 php bin/magento cron:run
   bxc2qly+ 25863  0.0  0.0  23724  2472 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe-bxc2qlykqhbqe
   bxc2qly+ 25876 53.0  0.6 475472 111468 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25878 57.0  0.6 475472 112080 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25880 50.5  0.6 475472 111312 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25882 48.5  0.6 475472 111220 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25884 50.5  0.6 475472 111372 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25890 32.5  0.6 475368 110672 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25892 34.5  0.6 475472 110724 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25894 31.5  0.6 475368 110136 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25896 29.0  0.6 475320 109876 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   ```

1. Si vous voyez une tâche [!DNL cron] longue qui peut être le processus de déploiement bloqué, vous pouvez arrêter le processus à l’aide de la commande `kill`. Vous pouvez identifier l’ **ID de processus** (colonne `PID` trouvée), puis placer cet `PID` dans la commande pour tuer le processus.
La commande **kill process** est la suivante :

   ```kill -9 <PID>```

1. Vous pouvez ensuite effectuer un redéploiement si vous tentez de le redéployer.
