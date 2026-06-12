---
title: '[!DNL Cron] tâche est bloquée au statut **en cours**'
description: Cet article fournit des solutions pour les cas où l’exécution des tâches Adobe Commerce n’est pas terminée et  [!DNL cron]  conserver un statut « en cours d’exécution », ce qui empêche l’exécution d [!DNL cron] autres tâches. Cela peut se produire pour de nombreuses raisons, telles que des problèmes réseau, des blocages d’applications, des problèmes de redéploiement.
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 40766238a7ea748bff86decf75cddec28fe63bb9
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# [!DNL Cron] tâche est bloquée au statut « en cours »

Cet article fournit des solutions pour les cas où l’exécution des tâches de [!DNL cron] Adobe Commerce ne se termine pas et conserve le statut « en cours », ce qui empêche l’exécution d’autres tâches de [!DNL cron]. Cela peut se produire pour de nombreuses raisons, telles que des problèmes réseau, des blocages d’applications, des problèmes de redéploiement.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud, toutes versions confondues

## Symptôme {#symptom}

Les symptômes des tâches [!DNL cron] qui doivent être réinitialisées incluent :

* De nombreuses tâches apparaissent dans la file d’attente de `cron_schedule`
* Les performances du site commencent à se dégrader
* Les traitements ne s’exécutent pas selon le calendrier

## Solutions {#solutions}

### Solution pour arrêter toutes les tâches [!DNL cron] à la fois {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>L’exécution de cette commande sans l’option `--job-code` réinitialise *toutes* les tâches [!DNL cron], y compris celles en cours d’exécution. Nous vous recommandons donc de l’utiliser uniquement dans des cas exceptionnels, par exemple après avoir vérifié que toutes les tâches [!DNL cron] doivent être réinitialisées. Le redéploiement exécute cette commande par défaut pour réinitialiser [!DNL cron] tâches afin qu’elles récupèrent correctement après la sauvegarde de l’environnement. Évitez d’utiliser cette solution lorsque les indexeurs sont en cours d’exécution.

Pour résoudre ce problème, vous devez réinitialiser la ou les tâches [!DNL cron] à l’aide de la commande `cron:unlock` . Cette commande modifie le statut de la tâche [!DNL cron] dans la base de données, mettant fin à la tâche de force pour permettre à d’autres tâches planifiées de continuer.

1. Ouvrez un terminal et utilisez vos [clés SSH](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/secure-connections) pour vous connecter à l’environnement affecté.
1. Obtenez les informations d’identification de la base de données MySQL : `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp`
1. Connectez-vous à la base de données à l’aide de `mysql` : `mysql -hdatabase.internal -uuser -ppassword main`
1. Sélectionnez la base de données `main` : `use main`
1. Rechercher tous les traitements de [!DNL cron] en cours d&#39;exécution : `SELECT * FROM cron_schedule WHERE status = 'running';`
1. Copiez le `job_code` de toute tâche exécutée plus longtemps que d’habitude.
1. Utilisez les identifiants de planification de l’étape précédente pour déverrouiller des tâches de [!DNL cron] spécifiques : `./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]`

### Solution pour arrêter une seule [!DNL cron] {#solution-stop-a-single-cron}

1. Ouvrez un terminal et utilisez vos [clés SSH](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/secure-connections) pour vous connecter à l’environnement affecté.
1. Vérifiez les tâches à long terme à l’aide de la commande suivante :

   `date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'`

1. Dans la sortie, comme dans l’exemple de sortie ci-dessous, vous verrez la date actuelle et la liste des processus. La colonne `START` affiche l’heure ou la date de début du processus :

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

1. Si vous constatez que des tâches de [!DNL cron] de longue durée peuvent bloquer le processus de déploiement, vous pouvez mettre fin au processus à l’aide de la commande `kill`. Vous pouvez identifier le **ID du processus** (dans la colonne `PID`), puis placer ce `PID` dans la commande pour interrompre le processus.
La commande **kill process** est la suivante :

   `kill -9 <PID>`

1. Vous pouvez ensuite effectuer un nouveau déploiement, si vous tentez d’effectuer un nouveau déploiement.
