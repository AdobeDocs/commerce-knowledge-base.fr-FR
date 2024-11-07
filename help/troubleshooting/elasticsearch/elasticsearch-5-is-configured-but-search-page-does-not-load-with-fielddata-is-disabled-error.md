---
title: Elasticsearch 5 est configuré, mais la page de recherche ne se charge pas avec l’erreur "Field data is disabled...".
description: "Cette rubrique décrit comment résoudre le problème avec Elasticsearch 5, où la page de recherche ne se charge pas, et l’exception similaire à la suivante est générée :"
exl-id: f5fa8144-4e7c-45ce-89d0-a8367e91d6db
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Elasticsearch 5 est configuré, mais la page de recherche ne se charge pas avec l’erreur &quot;Field data is disabled...&quot;.

Cette rubrique décrit comment résoudre le problème avec Elasticsearch 5, où la page de recherche ne se charge pas, et l’exception similaire à la suivante est générée :

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Versions affectées

* Adobe Commerce 2.2.x
* Elasticsearch v5

>[!NOTE]
>
>Elasticsearch v.5 est obsolète pour Adobe Commerce 2.3.x

## Problème

Conditions préalables : l’Elasticsearch 5 est configuré.

Lors de la demande de recherche, l’exception suivante est générée dans les journaux :

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Cause

Par défaut, seuls certains types d’attributs de produit peuvent être utilisés dans la navigation par couches. Il s’agit des options Oui/Non, Liste déroulante, Multisélection et Prix. C’est pourquoi, dans l’administrateur de Commerce, vous ne pouvez pas définir un attribut d’un autre type comme **Utiliser dans la navigation par couches** = *Filtrable* ou **Utiliser dans la navigation par couches des résultats de la recherche** = *Oui*. Cependant, il existe une possibilité technique de contourner cette limitation en modifiant directement les valeurs `is_filterable` et `is_filterable_in_search` dans la base de données. Si cela se produit, et que tout autre type d’attribut, tel que Date, Texte, etc., est défini pour être utilisé dans la navigation par couches, Elasticsearch 5 renvoie une exception.

Pour vous assurer que c’est le cas, vous devez déterminer s’il existe d’autres attributs que la liste déroulante, la sélection multiple et le prix, qui sont définis pour être utilisés dans la navigation par calques. Exécutez la requête suivante pour rechercher ces attributs :

```sql
SELECT ea.attribute_code, ea.frontend_input, cea.is_filterable, cea.is_filterable_in_search FROM eav_attribute AS ea
    -> INNER JOIN catalog_eav_attribute AS cea ON ea.attribute_id = cea.`attribute_id`
    -> WHERE (is_filterable = 1 OR is_filterable_in_search = 1) AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
```

Le résultat contiendra une liste des attributs utilisés pour la navigation par calques, dont le type ne permet pas cette opération. Suivez les étapes décrites dans la section suivante pour corriger ce problème.

## Solution

Pour résoudre le problème, vous devez définir `is_filterable` (utilisé dans la navigation par couches) et `filterable_in_search` (utilisé dans la navigation par couches dans les résultats de recherche) sur &quot;0&quot; (non utilisé). Pour ce faire, procédez comme suit :

1. Créez une sauvegarde de base de données.
1. Utilisez un outil de base de données tel que [phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) ou accédez manuellement à la base de données à partir de la ligne de commande pour exécuter la requête SQL suivante :

   ```sql
   UPDATE catalog_eav_attribute AS cea
       INNER JOIN eav_attribute AS ea
           ON ea.attribute_id = cea.attribute_id
   SET cea.is_filterable = 0, cea.is_filterable_in_search = 0
   WHERE (cea.is_filterable = 1 OR cea.is_filterable_in_search = 1)
       AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
   ```

1. Exécutez la réindexation complète de la recherche catalogue à l’aide de la commande suivante :

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Nettoyer le cache en cours d’exécution

   ```bash
   bin/magento cache:clean
   ```

ou dans l’administrateur Commerce sous **System** > **Tools** > **Cache Management**.

Vous devriez maintenant pouvoir effectuer des recherches de catalogue sans problème.
