---
title: Recherche de tables MySQL volumineuses
description: '''Pour identifier les tables volumineuses, connectez-vous à la base de données comme décrit dans l''article [Se connecter à la base de données](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database), puis exécutez la commande suivante, où `project_id` correspond à votre ID de projet Cloud :'''
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Recherche de tables MySQL volumineuses

Pour identifier les grandes tables, connectez-vous à la base de données comme décrit dans la section [Connexion à la base de données](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) et exécutez la commande suivante, où `project_id` correspond à votre ID de projet Cloud :

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Cela afficherait la liste complète des tableaux et leur taille. Vous pouvez parcourir la liste et identifier les tables qui nécessitent une attention en raison de leur taille.
