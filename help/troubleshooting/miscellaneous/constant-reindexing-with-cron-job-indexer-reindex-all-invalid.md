---
title: Les index invalidés et "indexer_reindex_all_invalid" s’exécutent constamment.
description: Les index invalidés et "indexer_reindex_all_invalid" s’exécutent constamment.
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Index invalidés et `indexer_reindex_all_invalid` exécutés en permanence

Cet article fournit une solution possible au problème lorsque les problèmes de performances de votre site sont dus à une réindexation constante. Cela est dû à la tâche [!DNL cron] `indexer_reindex_all_invalid` qui s’exécute en continu et aux caches nettoyés sur [!DNL reindex].

## Produits et versions concernés

* Adobe Commerce (cloud et sur site) 2.4.0+ (comme **[!UICONTROL Category Permissions]** est une fonctionnalité Commerce Adobe uniquement, cela n’affecte pas le Magento Open Source.)

## Problème

Dans [!DNL New Relic One], les journaux d’erreurs doivent afficher `indexer_update_all_views` s’exécutant plusieurs fois avec une durée supérieure à 1 seconde (c’est-à-dire qu’il traite quelque chose).

## Cause

Lorsque l’importateur Adobe Commerce principal est exécuté (manuellement ou par [!DNL cron]), un ensemble de modules externes sur plusieurs modules principaux est exécuté pour déterminer les index qui doivent être invalidés.

Le problème se produit lorsque le module **[!UICONTROL Category Permissions]** est activé dans [!DNL Commerce Admin]. Si cela est vrai, le module externe du module invalide toujours les index Produit et Catégorie (et les index liés) lorsqu’un import est exécuté. Si les types d’importation standard sont examinés, ils ont tous une incidence sur **[!UICONTROL Category Permissions]**. L’invalidation est attendue.

En outre, lorsqu’un site a des modules B2B activés, si **[!UICONTROL Shared Catalog]** est activé, il s’active et verrouille **[!UICONTROL Category Permissions]**. La désactivation de **[!UICONTROL Shared Catalog]** déverrouille **[!UICONTROL Category Permissions]**, mais ne la désactive pas.

<u>Vérifiez que [!DNL cron] se connecte à votre base de données [!DNL MySQL]</u> :

Si vous vous connectez à votre base de données [!DNL MySQL], ils peuvent vérifier votre journal `cron` pour le processus **[!DNL reindex all indexes]**.
Ce **should** apparaît plusieurs fois, mais le facteur important est que le processus effectue l’une des deux tâches possibles.

Le processus ne peut effectuer qu’une des deux opérations suivantes :

1. Rien : cela prendrait 0 à 1 seconde (une seconde ou moins) - le processus vérifie s’il a besoin de faire quoi que ce soit, puis s’arrête s’il n’a pas besoin de faire quoi que ce soit.
1. [!DNL Reindex] tout : cela prendra toujours du temps, généralement quelques minutes.

Normalement, vous souhaitez voir de nombreuses occurrences du processus, mais avec un temps d’exécution inférieur à 1 seconde.
Un commerçant peut donc utiliser cette requête [!DNL MySQL] pour rechercher les transactions dont l&#39;exécution prend **plus d&#39;une seconde** :

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

Vous pouvez voir la durée pendant laquelle une période est enregistrée en exécutant :

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Si cela ne vous donne pas une période suffisamment longue pour effectuer une évaluation appropriée, vous pouvez augmenter le temps de conservation d’un processus `cron` réussi dans le journal suivant ce guide [[!DNL Cron] (tâches planifiées)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) et augmenter la valeur **[!DNL Success History Lifetime]** (la valeur par défaut est de seulement 60 minutes).


## Solution

Étendez `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` de sorte que la méthode `afterImportSource` exclut l’importateur personnalisé.

```
    public function afterImportSource(\Magento\ImportExport\Model\Import $subject, $import)
    {
        if ($this->config->isEnabled() && $subject->getEntity() !== 'ENTITY_CODE') {
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Category::INDEXER_ID)->invalidate();
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Product::INDEXER_ID)->invalidate();
        }
        return $import;
    }
```

Où `ENTITY_CODE` est la valeur utilisée pour le paramètre de nom d’entité dans le fichier `import.xml` de l’importateur personnalisé.

## Lecture connexe

[Configurez [!DNL cron] jobs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) dans le Guide de configuration des opérations Adobe Commerce.
