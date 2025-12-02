---
title: Créer une image mémoire de base de données sur Adobe Commerce sur l’infrastructure cloud
description: Cet article présente les méthodes possibles (et recommandées) de création d’une image mémoire de base de données (DB) sur Adobe Commerce dans une infrastructure cloud.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 96b145a1f76c296907da96fd97c7a8f7778463f8
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Créer une image mémoire de base de données sur Adobe Commerce sur l’infrastructure cloud

Cet article présente les méthodes possibles (et recommandées) de création d’une image mémoire de base de données (DB) sur Adobe Commerce dans une infrastructure cloud.

Il vous suffit d’utiliser une seule variante (option) pour vider votre base de données. Ces options s’appliquent à tout type d’environnement (intégration, évaluation, production) et à tout plan (architecture du plan de démarrage de l’infrastructure cloud d’Adobe Commerce et architecture du plan Pro de l’infrastructure cloud d’Adobe Commerce).

## Prérequis : SSH dans votre environnement

Pour vider votre base de données sur Adobe Commerce sur une infrastructure cloud avec n’importe quelle variante abordée dans cet article, vous devez d’abord [SSH à votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=fr).

>[!WARNING]
>
>Que vous choisissiez l’option 1 ou l’option 2, exécutez la commande pendant les heures creuses sur un nœud secondaire de base de données.

## Option 1 : db-dump (**ece-tools ; recommandé**)

Vous pouvez vider votre base de données à l&#39;aide de la commande [ECE-Tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=fr) :

```php
vendor/bin/ece-tools db-dump
```

Il s’agit de l’option recommandée et la plus sûre.

Voir [Dump your database (ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html?lang=fr) dans notre guide Commerce on Cloud Infrastructure.

## Option 2 : mariadb-dump (ou mysqldump pour les versions plus anciennes)

+++<b>Pour les nouvelles versions de MariaDB (11.x et ultérieures)</b>

À partir de MariaDB 11.0.1, le lien symbolique `mysqldump` est obsolète. Il est recommandé d’utiliser `mariadb-dump` à la place.

Pour plus d’informations, consultez la section [utilitaire client mariadb-dump](https://mariadb.com/docs/server/clients-and-utilities/backup-restore-and-import-clients/mariadb-dump).

+++

+++<b>Pour les anciennes versions de MariaDB</b> 

Si vous utilisez une ancienne version de MariaDB, mais que `mariadb-dump` n’est pas disponible, vous pouvez vider votre base de données à l’aide de la commande MySQL `mysqldump` native.

>[!WARNING]
>
>N’exécutez pas cette commande sur le cluster de base de données. Le cluster ne différencie pas s’il est exécuté sur la base de données principale ou sur une base de données secondaire. Si le cluster exécute cette commande sur l’instance principale, la base de données ne peut pas exécuter d’écritures tant que l’image mémoire n’est pas terminée et peut avoir un impact sur les performances et la stabilité du site.

La commande entière peut se présenter comme suit :

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

La sauvegarde de la base de données créée en exécutant la commande `mysqldump` et enregistrée dans `\tmp` doit être déplacée à partir de cet emplacement. Il ne doit pas occuper d’espace de stockage dans `\tmp` (ce qui peut entraîner des problèmes).

+++

Pour obtenir vos informations d’identification de base de données (hôte, nom d’utilisateur et mot de passe), vous pouvez appeler la variable d’environnement `MAGENTO_CLOUD_RELATIONSHIPS` :

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Documentation connexe :**

* [mysqldump - Programme de sauvegarde de la base de données](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) dans la documentation officielle de MySQL.
* [Variables spécifiques au cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html?lang=fr) (voir `MAGENTO_CLOUD_RELATIONSHIPS`) dans notre guide Commerce sur les infrastructures cloud.
