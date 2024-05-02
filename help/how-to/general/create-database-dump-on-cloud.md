---
title: Création d’un vidage de base de données sur Adobe Commerce sur l’infrastructure cloud
description: Cet article décrit les méthodes possibles (et recommandées) pour créer un vidage de base de données (DB) sur Adobe Commerce sur l’infrastructure cloud.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 0948b2a94ee4f2a355e7c024a09929f0ad223783
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Création d’un vidage de base de données sur Adobe Commerce sur l’infrastructure cloud

Cet article décrit les méthodes possibles (et recommandées) pour créer un vidage de base de données (DB) sur Adobe Commerce sur l’infrastructure cloud.

Vous ne devez utiliser qu’une seule variante (option) pour vider votre base de données. Ces options s’appliquent à n’importe quel type d’environnement (intégration, évaluation, production) et à n’importe quel plan (architecture du plan de démarrage pour l’infrastructure cloud d’Adobe Commerce et architecture du plan de planification d’Adobe Commerce sur l’infrastructure cloud Pro).

## Condition préalable : SSH vers votre environnement

Pour vider votre base de données sur Adobe Commerce sur l’infrastructure cloud avec toute variante abordée dans cet article, vous devez d’abord [SSH vers votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).

>[!WARNING]
>
>Si vous choisissez Option 1 ou Option 2, exécutez la commande en dehors des heures de pointe sur un noeud secondaire de base de données.

## Option 1 : db-dump (**outil de création de pièces, recommandé**)

Vous pouvez vider votre base de données à l’aide du [CEE-Outils](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) command :

```php
vendor/bin/ece-tools db-dump
```

Il s’agit de l’option recommandée et la plus sûre.

Voir [Videz votre base de données (Outils d’évaluation)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html) dans notre guide Commerce on Cloud Infrastructure.

## Option 2 : mysqldump

>[!WARNING]
>
>N’exécutez pas cette commande sur la grappe de base de données. La grappe ne fait pas la distinction entre l’exécution sur la base de données principale et l’exécution sur une base secondaire. Si la grappe exécute cette commande sur l’instance principale, la base de données ne peut pas exécuter les écritures tant que la vidage n’est pas terminée et peut avoir une incidence sur les performances et la stabilité du site.

Vous pouvez vider votre base de données à l’aide du MySQL natif. `mysqldump` .

La commande entière peut se présenter comme suit :

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

Sauvegarde de base de données créée lors de l’exécution de la fonction `mysqldump` et enregistrés dans `\tmp`, doit être déplacé de cet emplacement. Il ne doit pas prendre d’espace de stockage dans `\tmp` (ce qui peut entraîner des problèmes).

Pour obtenir vos informations d’identification DB (hôte, nom d’utilisateur et mot de passe), vous pouvez appeler la fonction `MAGENTO_CLOUD_RELATIONSHIPS` Variable d’environnement :

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Documentation connexe :**

* [mysqldump - Un programme de sauvegarde de base de données](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) dans la documentation officielle de MySQL.
* [Variables spécifiques au cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html) (voir `MAGENTO_CLOUD_RELATIONSHIPS`) dans notre guide Commerce on Cloud Infrastructure.
