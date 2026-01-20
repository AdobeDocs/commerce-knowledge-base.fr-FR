---
title: Valeur numérique de base de données Adobe Commerce hors plage, « INT » à « BIGINT »
description: Cet article fournit des solutions pour les cas où vous ne pouvez pas enregistrer une mise à jour d’un produit, comme une modification de prix, ou supprimer et dupliquer un produit.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 5ca7a4400e62db2419b32a31a4f6cf04f5a82e35
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Valeur numérique de base de données Adobe Commerce hors plage, `INT` à `BIGINT`

>[!WARNING]
>
>Avant de mettre en œuvre la solution décrite dans cet article (`INT` à `BIGINT` mise à jour du schéma), les commerçants doivent toujours vérifier que le champ qu’ils vont modifier NE possède AUCUNE relation de clé étrangère avec une autre table. Si le champ possède des relations de clé étrangère avec une autre table, des problèmes se produiront car le champ associé est toujours `INT`. Il peut utiliser la requête suivante pour vérifier cela. Cette requête répertorie les relations de clé étrangère disponibles dans la base de données pour le champ de table donné :
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

Cet article fournit des solutions pour les cas où vous ne pouvez pas enregistrer une mise à jour d’un produit, comme une modification de prix, ou supprimer et dupliquer un produit.
Le message d&#39;erreur *L&#39;enregistrement de l&#39;article stocké a échoué) s&#39;affiche. Veuillez réessayer.* Il se peut que le déploiement échoue après une mise à jour du produit. Il se peut également que le message d’erreur [!DNL MySQL] suivant s’affiche lorsque vous exécutez `php bin/magento setup:upgrade` (sur Adobe Commerce sur les infrastructures cloud, cette erreur s’affiche dans les journaux de déploiement) :

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

Les solutions décrites dans l’article sont les suivantes :
* Mettez à jour la `[ AUTO_INCREMENT ]` à la valeur suivante dans le tableau ou
* `INT` à `BIGINT` mise à jour du schéma

La solution que vous utilisez dépend de la cause du problème. Référez-vous aux étapes ci-dessous pour isoler la cause.

## Étapes de vérification de la cause


Vérifiez la valeur la plus élevée de la clé primaire en exécutant la commande suivante dans le terminal : `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Si la `max(value_id)` est inférieure à la `max int(11) [ 4294967296 ]` et que la `[ AUTO_INCREMENT ]` a une valeur supérieure ou égale à la `max int(11) [ 4294967296 ]`, envisagez de [mettre à jour la `[ AUTO_INCREMENT ]` à la valeur suivante du tableau](#update-the-auto-increment-to-the-next-value-from-the-table). Sinon, envisagez une [`INT` pour `BIGINT` mise à jour du schéma](#int_to_bigint_schema_update).

## Mettez à jour la `AUTO_INCREMENT` à la valeur suivante dans le tableau {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Effectuez une sauvegarde de la base de données avant de modifier les tables. Mettez également le site en [mode de maintenance](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). En outre, il est également recommandé d’exécuter la commande [!DNL MySQL] optimizer sur les tables de la base de données (uniquement sur les tables où des modifications ont été apportées) après avoir effectué les modifications.

>[!NOTE]
>
>Le site doit être en mode de maintenance lors de l&#39;exécution de la commande d&#39;optimisation sur des tables spécifiques. Cette opération reconstruit complètement les tables et libère de l&#39;espace après la suppression des données des tables.

Si la valeur affichée est inférieure à `max int(11) [ 4294967296 ]`, comme le montre l&#39;exemple de sortie de terminal ci-dessous, un tableau `[ AUTO_INCREMENT ]` a été modifié en un nombre plus grand ou égal à la valeur `max [ int(11) ]`.

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

Comme vous pouvez le voir dans l’exemple de sortie ci-dessus, la `[ AUTO_INCREMENT ]` du tableau a été remplacée par un nombre plus grand que la `max int(11) [ 4294967296 ]`. La solution consiste à mettre à jour le `[ AUTO_INCREMENT]` à la valeur suivante du tableau :

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## `INT` à `BIGINT` mise à jour du schéma {#int_to_bigint_schema_update}

Cependant, si lors de l’exécution de la requête suivante `SELECT MAX(value_id) FROM catalog_product_entity_int;` la valeur affichée est supérieure à , `max int(11) [ 4294967296 ]` envisagez d’effectuer une `INT` à `BIGINT` mise à jour du schéma . Le type de données `BIGINT` a une plage de valeurs plus large.

Pour ce faire :

1. Créez un module personnalisé dans le répertoire *app/code/*.
1. Dans le module personnalisé, créez un fichier *db_schema.xml*. Dans *db_schema.xml* définissez le type de données sur `BIGINT`.
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

* [Instructions générales [!DNL MySQL] &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) dans le Guide d’installation de Commerce
* [&#x200B; Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur les infrastructures cloud &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html) dans notre base de connaissances d’assistance
* [Problèmes de base de données les plus courants dans Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) dans notre base de connaissances d’assistance
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
