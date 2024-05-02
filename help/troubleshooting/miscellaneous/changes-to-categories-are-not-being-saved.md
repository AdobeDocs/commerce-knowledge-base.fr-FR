---
title: Les modifications apportées aux catégories ne sont pas enregistrées.
description: Cet article fournit un correctif pour la mise à jour des catégories de produits via l’administrateur Commerce. Les modifications ne s’affichent pas sur l’administrateur et le storefront. Le problème est dû aux données corrompues de la table `catalog_category_entity`. Pour résoudre ce problème, corrigez ou supprimez les enregistrements de mise à jour de catégorie problématiques dans le tableau. Ensuite, vous devriez pouvoir mettre à jour les catégories de produits à l’aide de l’administrateur.
exl-id: d951205c-add9-478c-9c7d-2ba975d53b14
feature: Categories
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---

# Les modifications apportées aux catégories ne sont pas enregistrées.

Cet article fournit un correctif pour la mise à jour des catégories de produits via l’administrateur Commerce. Les modifications ne s’affichent pas sur l’administrateur et le storefront. Le problème est dû aux données corrompues dans la variable `catalog_category_entity` table. Pour résoudre ce problème, corrigez ou supprimez les enregistrements de mise à jour de catégorie problématiques dans le tableau. Ensuite, vous devriez pouvoir mettre à jour les catégories de produits à l’aide de l’administrateur.

## Problème

Après avoir apporté des modifications à une catégorie de produits dans l’Admin et l’enregistrement, les nouvelles mises à jour ne sont ni enregistrées, ni affichées dans l’Admin et le storefront.

### Étapes à reproduire

1. Accédez à **Catalogue** > **Catégories**.
1. Sélectionnez une catégorie.
1. Effectuez les modifications, puis cliquez sur **Enregistrer**.
1. Le message s&#39;affiche : *Vous avez enregistré la catégorie*.
1. Notez que la modification que vous avez effectuée n’a pas été enregistrée.

## Cause possible : données corrompues dans la variable `catalog_category_entity` table

Le problème est causé par les mêmes valeurs dans la variable `created_in` colonne des enregistrements de catégorie concernée dans la base de données (DB).

![Données endommagées dans la table catalog_category_entity](assets/catalog_category_entity.png)

Détails :

* La variable `catalog_category_entity` La table DB comporte au moins deux enregistrements pour la catégorie affectée (ces enregistrements ont le même `entity_id` ).
* Ces enregistrements de catégorie comportent les éléments suivants : **les mêmes valeurs dans la variable `created_in` column**.

### Comment la deuxième entrée DB (et toutes les entrées suivantes) apparaît-elle dans DB pour une catégorie et une même catégorie ?

Le deuxième enregistrement DB (et, éventuellement, les suivants) pour la catégorie affectée signifie qu’il y a eu des mises à jour de catégorie planifiées à l’aide du module Magento\_Staging . Le module crée un enregistrement supplémentaire pour une catégorie dans la variable `catalog_category_entity` et c’est le comportement attendu de l’application ; le problème est que les enregistrements ont les mêmes valeurs pour la variable `created_in` colonne .

### Comment apparaissent les mêmes valeurs ?

Nous ne pouvons expliquer avec certitude les raisons de la corruption des données. Les raisons possibles peuvent être les suivantes :

* personnalisations (code, thèmes, etc.)
* migration incorrecte des données
* restauration des données incorrectes à partir de la sauvegarde

À notre connaissance, cette corruption de données n’est pas typique pour l’instance Adobe Commerce &quot;propre&quot; (prête à l’emploi) et ne peut pas être reproduite sur une installation Adobe Commerce sans personnalisation.

### Comment vérifier que c&#39;est votre problème

La variable `catalog_category_entity` doit comporter plusieurs enregistrements pour la catégorie affectée (les enregistrements doivent avoir le même `entity_id` ) et au moins deux de ces enregistrements doivent avoir la même valeur `created_in` valeurs. Ainsi, les mises à jour planifiées par évaluation ne s’afficheraient pas dans l’administrateur Commerce ; vous ne verriez que le bloc Modifications planifiées vide.

#### Étapes à vérifier

1. Accédez à la table catalog\_category\_entity dans votre base de données.
1. Filtrez les entités par entity\_id, avec entity\_id identifiant la catégorie affectée.
1. Si les valeurs de la colonne created\_in sont identiques pour différentes entrées ayant le même entity\_id, c’est notre cas. Normalement, la variable `created_in` sont différentes pour chaque enregistrement.

![Données endommagées dans la table catalog_category_entity](assets/catalog_category_entity.png)

## Solution

Vous pouvez choisir l’une des solutions suivantes :

1. **Supprimer** les enregistrements de mise à jour de catégorie problématiques ;
1. **Réparer** les enregistrements de mise à jour de catégorie problématiques ;

### Supprimer les enregistrements de mise à jour de catégorie problématiques

Dans cette solution, vous devrez définir la variable `updated_in` pour l’enregistrement de catégorie initial et supprimez tous les autres enregistrements pour cette catégorie. Cette opération supprime toutes les mises à jour de catégorie planifiées.

Procédez comme suit :

1. Recherchez les enregistrements de la base de données à l’aide de la méthode `entity_id` de la catégorie affectée.
1. Sélectionnez l’enregistrement avec le plus grand entier dans la variable `updated_in` colonne .
1. Copiez le `updated_in` de l’enregistrement sélectionné.
1. Sélectionner l’enregistrement avec `row_id` = `entity_id` (enregistrement de catégorie initial) et collez la valeur copiée dans le `updated_in` de cet enregistrement.
1. Supprimer la ou les rangées avec `row_id` différent de `entity_id` .

### Réparer les enregistrements de mise à jour de catégorie problématiques

1. Rechercher les enregistrements de catégorie avec le même `entity_id` et identique `created_in` .
1. Sélectionnez l’enregistrement où `row_id` = `entity_id` et copiez la variable `updated_in` .
1. Sélectionnez l’enregistrement où `row_id` n’est pas égal à `entity_id` et collez le code copié `updated_in` comme valeur de `created_in` . Reportez-vous à la capture d’écran ci-dessous comme illustration.    ![Copie du fichier created_in value.png](assets/copy_created-in_value.png)
1. Vérifiez que l’enregistrement de mise à jour de catégorie, le `created_in` dont vous avez mis à jour la valeur (à l’étape 3), figure dans la variable `staging_update` table. *Par exemple :* Si la variable copiée `created_in` est 1509281953, ALORS l’entité avec `row_id` = 1509281953 doit exister dans la variable `staging_update` table
