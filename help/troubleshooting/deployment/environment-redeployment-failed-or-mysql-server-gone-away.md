---
title: Échec du redéploiement de l’environnement ou disparition du serveur MySQL
description: Cet article fournit une solution aux problèmes d’Adobe Commerce (toutes les méthodes de déploiement), où la panne d’espace alloué à MySQL entraîne des erreurs de déploiement bloquées ou de connexion à la base de données.
exl-id: 2086b45a-0bfe-45cc-bef9-1b6f09ddb70a
feature: Deploy, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Échec du redéploiement de l’environnement ou disparition du serveur MySQL

Cet article fournit une solution aux problèmes d’Adobe Commerce (toutes les méthodes de déploiement), où la panne d’espace alloué à MySQL entraîne des erreurs de déploiement bloquées ou de connexion à la base de données.

## Produits et versions concernés

* Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud (toutes versions)

## Problème

* Le processus de déploiement échoue avec l’erreur suivante dans le journal de déploiement (ligne de commande et journal de l’interface utilisateur) : ```bash    Re-deploying environment abcdefghijklm-master-7rqtwti         E: Environment redeployment failed    ```
* Adobe Commerce répond avec l’erreur 503 et le message d’erreur suivant s’affiche dans les logs de l’application :    ```bash    SQLSTATE[HY000] [2006] MySQL server has gone away    ```    et l’erreur suivante s’affiche lorsque vous vous connectez à un serveur MySQL :    ```bash    ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"    ```

## Cause

La cause la plus probable des problèmes est que l’espace alloué à la base de données MySQL est trop faible. Pour vous assurer que c’est le cas, vérifiez l’espace disponible pour MySQL comme décrit plus loin.

### Vérifiez s’il y a assez d’espace pour MySQL.

Pour tous les environnements d’architecture de plan de démarrage de l’infrastructure cloud d’Adobe Commerce et l’[environnement d’intégration](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) de l’architecture de plan Adobe Commerce on cloud Infrastructure Pro, [SSH to the environment](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=fr) et exécutez la commande :

```bash
magento-cloud db:size
```

Pour l’environnement d’évaluation ou de production de l’architecture Pro, [SSH vers l’environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=fr) et exécutez le `df -h`   commande `| grep mysql`. Le résultat ressemblera à ce qui suit :

```bash
sxpe7gigd5ok2@i-00baa9e24f31dba41:~$ df -h | grep mysql
/dev/xvdj                            40G  7.4G   32G  19% /data/mysql
```

## Solution

### Pour résoudre ce problème, vous devez allouer plus d’espace pour MySQL.

Pour tous les environnements d’intégration d’architecture Starter et Pro, cette opération est effectuée dans le fichier `.magento/services.yaml` en augmentant le paramètre `mysql: disk:`. Par exemple :

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Voir l’article [Configuration du service MySQL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html?lang=fr) à titre de référence.

Pour apporter ces modifications à l’environnement d’évaluation ou de production de l’architecture Pro, vous devez créer un [ticket d’assistance](https://support.magento.com). En règle générale, vous n’aurez pas à gérer cela sur l’évaluation/la production de l’architecture Pro, car Adobe Commerce surveille ces paramètres pour vous et vous alerte et/ou prend des mesures conformément au contrat.

### Application des modifications

Une fois que vous avez modifié le fichier `.magento/services.yaml`, vous devez valider et envoyer vos modifications pour qu’elles soient appliquées. La notification push déclenche le processus de déploiement.
