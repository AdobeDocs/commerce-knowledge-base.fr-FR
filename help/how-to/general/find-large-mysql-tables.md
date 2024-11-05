---
title: Recherche de tables MySQL volumineuses
description: '''Pour identifier les tables volumineuses, connectez-vous à la base de données comme décrit dans l''article [Se connecter à la base de données](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database), puis exécutez la commande suivante, où `project_id` correspond à votre ID de projet Cloud :'''
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Recherche de tables MySQL volumineuses

Pour identifier les tables volumineuses, connectez-vous à la base de données comme décrit dans l’article [Se connecter à la base de données](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) et exécutez la commande suivante, où `project_id` est votre ID de projet Cloud :

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Cela afficherait la liste complète des tableaux et leur taille. Vous pouvez parcourir la liste et identifier les tables qui nécessitent une attention en raison de leur taille.

## Lecture connexe

[ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
