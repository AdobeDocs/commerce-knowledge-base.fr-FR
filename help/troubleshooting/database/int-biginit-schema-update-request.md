---
title: Valeur numérique hors plage de la base de données Adobe Commerce, "INT" par "BIGINT"
description: Cet article fournit des solutions pour les cas où vous ne pouvez pas enregistrer une mise à jour de produit, telle qu’une modification de prix, ou la suppression et la duplication d’un produit.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Valeur numérique hors plage de la base de données Adobe Commerce, `INT` à `BIGINT`

>[!WARNING]
>
>Avant d’implémenter la solution dans cet article (`INT` vers `BIGINT` mise à jour du schéma), les marchands doivent toujours vérifier que le champ qu’ils vont modifier N’A AUCUNE relation de clé étrangère avec une autre table. Si le champ a des relations de clé étrangère avec une autre table, des problèmes se produiront car le champ associé est toujours `INT`. Ils peuvent utiliser la requête suivante pour vérifier cela. Cette requête répertorie les relations de clé étrangère disponibles dans la base de données pour le champ de table donné :
>
>```mysql
>SELECT 
>     TABLE_NAME,COLUMN_NAME,CONSTRAINT_NAME,REFERENCED_TABLE_NAME,REFERENCED_COLUMN_NAME
>FROM
>   INFORMATION_SCHEMA.KEY_COLUMN_USAGE
>WHERE
>     REFERENCED_TABLE_SCHEMA = '<database_name>' AND
>     REFERENCED_TABLE_NAME = '<table_name>' AND
>     REFERENCED_COLUMN_NAME = '<table_field>';
>```

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

Cet article fournit des solutions pour les cas où vous ne pouvez pas enregistrer une mise à jour de produit, telle qu’une modification de prix, ou la suppression et la duplication d’un produit.
Le message d&#39;erreur *L&#39;article de stock n&#39;a pas pu être enregistré s&#39;affiche. Veuillez réessayer.* Le déploiement peut échouer après la mise à jour d’un produit. Vous pouvez également voir le message d’erreur [!DNL MySQL] suivant lorsque vous exécutez `php bin/magento setup:upgrade` (sur Adobe Commerce sur l’infrastructure cloud, cette erreur s’affiche dans les journaux de déploiement) :

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

Les solutions décrites dans cet article sont les suivantes :
* Mettez à jour `[ AUTO_INCREMENT ]` vers la valeur suivante de la table ou
* Mise à jour du schéma `INT` vers `BIGINT`

La solution que vous utilisez dépend de ce qui a causé le problème. Reportez-vous aux étapes ci-dessous pour isoler la cause.

## Étapes pour vérifier la cause


Vérifiez la valeur la plus élevée de la clé primaire en exécutant la commande suivante dans le terminal : `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Si `max(value_id)` est inférieur à `max int(11) [ 4294967296 ]` et que `[ AUTO_INCREMENT ]` a une valeur supérieure ou égale à `max int(11) [ 4294967296 ]`, envisagez de [mettre à jour `[ AUTO_INCREMENT ]` vers la valeur suivante de la table](#update-the-auto-increment-to-the-next-value-from-the-table). Dans le cas contraire, envisagez une mise à jour de schéma [`INT` vers `BIGINT` &#x200B;](#int_to_bigint_schema_update).

## Mettre à jour `AUTO_INCREMENT` vers la valeur suivante de la table {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Effectuez une sauvegarde de la base de données avant de modifier les tables. Placez également le site en [mode de maintenance](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html?lang=fr#maintenance-mode). En outre, il est également recommandé d’exécuter la commande [!DNL MySQL] optimize sur les tables de base de données (uniquement sur les tables où des modifications ont été apportées) après avoir apporté les modifications.

>[!NOTE]
>
>Le site doit être en mode de maintenance lors de l’exécution de la commande d’optimisation sur des tables spécifiques. Cette opération reconstruit complètement les tables et libère de l’espace après la suppression des données des tables.

Si la valeur affichée est inférieure à `max int(11) [ 4294967296 ]` comme illustré dans l’exemple de sortie de terminal ci-dessous, un tableau `[ AUTO_INCREMENT ]` a été remplacé par un nombre plus grand ou égal à la valeur `max [ int(11) ]`.

```mariadb
MariaDB [xxx]> SELECT MAX(value_id) FROM catalog_product_entity_int;
+---------------------+
| MAX(source_item_id) |
+---------------------+
|          4283174130 |
+---------------------+
```

Pour vérifier si cela s’est produit, exécutez la commande suivante dans le terminal :

```
MariaDB [xxx]> show create table catalog_product_entity_int;

...
) ENGINE=InnoDB AUTO_INCREMENT=4294967297 DEFAULT CHARSET=utf8 COMMENT='Catalog Product Integer Attribute Backend Table';
```

Comme vous pouvez le voir dans l’exemple de sortie ci-dessus, la table `[ AUTO_INCREMENT ]` a été remplacée par un nombre supérieur à `max int(11) [ 4294967296 ]`. La solution consiste à mettre à jour la valeur `[ AUTO_INCREMENT]` vers la valeur suivante de la table :

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## Mise à jour du schéma `INT` vers `BIGINT` {#int_to_bigint_schema_update}

Cependant, si, lors de l’exécution de la requête suivante `SELECT MAX(value_id) FROM catalog_product_entity_int;`, la valeur affichée est supérieure à `max int(11) [ 4294967296 ]`, envisagez d’effectuer une mise à jour de schéma `INT` vers `BIGINT`. Le type de données `BIGINT` possède une plus grande plage de valeurs.

Pour ce faire :

1. Créez un module personnalisé dans le répertoire *app/code/*.
1. Dans le module personnalisé, créez un *db_schema.xml*. Dans *db_schema.xml*, vous définissez le type de données sur `BIGINT`.
1. Ajoutez le contenu suivant, puis exécutez `bin/magento setup:upgrade` pour appliquer les modifications ci-dessus au tableau correspondant.

```
<?xml version="1.0"?>
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
    <table name="catalog_product_entity_int">
        <column xsi:type="bigint" name="value_id" unsigned="false" nullable="false" identity="true"
                comment="Value ID"/>
    </table>
</schema>
```


## Lecture connexe

* [Général [!DNL MySQL] conseils](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html?lang=fr) dans le Guide d’installation de Commerce
* [Le chargement de la base de données perd la connexion à [!DNL MySQL]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html?lang=fr) dans notre base de connaissances de support
* [Bonnes pratiques de base de données pour Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html?lang=fr) dans notre base de connaissances de support
* [Problèmes de base de données les plus courants dans Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html?lang=fr) dans notre base de connaissances de support
* [&#x200B; Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
