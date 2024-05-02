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

# Index invalidés et `indexer_reindex_all_invalid` run

Cet article fournit une solution possible au problème lorsque les problèmes de performances de votre site sont dus à une réindexation constante. Cela est dû au [!DNL cron] job `indexer_reindex_all_invalid` en cours d’exécution et nettoyage continu des caches [!DNL reindex].

## Produits et versions concernés

* Adobe Commerce (cloud et sur site) 2.4.0+ (en tant que **[!UICONTROL Category Permissions]** est une fonctionnalité d’Adobe Commerce uniquement, elle n’affecte pas le Magento Open Source.)

## Problème

Dans [!DNL New Relic One] les journaux d’erreurs doivent afficher `indexer_update_all_views` s’exécute plusieurs fois avec une durée supérieure à 1 seconde (c’est-à-dire qu’il traite quelque chose).

## Cause

Lorsque l’importateur Adobe Commerce principal est exécuté (manuellement ou par [!DNL cron]), un ensemble de modules externes à travers plusieurs modules principaux est exécuté pour déterminer les index qui doivent être invalidés.

Le problème survient lorsque la variable **[!UICONTROL Category Permissions]** est activé dans la variable [!DNL Commerce Admin]. Si cela est vrai, le module externe du module invalide toujours les index Produit et Catégorie (et les index liés) lorsqu’un import est exécuté. Si les types d’importation standard sont examinés, ils ont tous une incidence. **[!UICONTROL Category Permissions]**. L’invalidation est attendue.

En outre, lorsqu’un site dispose de modules B2B activés, si **[!UICONTROL Shared Catalog]** est activé, il s’active et verrouille **[!UICONTROL Category Permissions]**. Désactivation **[!UICONTROL Shared Catalog]** se déverrouille **[!UICONTROL Category Permissions]**, mais ne l’éteignez pas.

<u>Vérification [!DNL cron] se connecte à [!DNL MySQL] base</u>:

Si vous vous connectez à [!DNL MySQL] base de données, il peut vérifier vos `cron` journal de la variable **[!DNL reindex all indexes]** processus.
Ceci **should** apparaissent plusieurs fois, mais le facteur important est que le processus fait l&#39;une des deux choses possibles.

Le processus ne peut effectuer qu’une des deux opérations suivantes :

1. Rien : cela prendrait 0 à 1 seconde (une seconde ou moins) - le processus vérifie s’il a besoin de faire quoi que ce soit, puis s’arrête s’il n’a pas besoin de faire quoi que ce soit.
1. [!DNL Reindex] tout : ça prendra toujours du temps, en général quelques minutes.

Normalement, vous souhaitez voir de nombreuses occurrences du processus, mais avec un temps d’exécution inférieur à 1 seconde.
Un commerçant peut donc utiliser ceci : [!DNL MySQL] Requête pour rechercher les transactions qui prennent **plus d’une seconde** pour exécuter :

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

Vous pouvez voir la durée pendant laquelle une période est enregistrée en exécutant :

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Si cela ne vous donne pas un délai assez long pour effectuer une évaluation appropriée, vous pouvez augmenter le temps de réussite d’une `cron` Le processus est conservé dans le journal après cette opération [[!DNL Cron] (tâches planifiées)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) et d’augmenter le **[!DNL Success History Lifetime]** (la valeur par défaut est de 60 minutes uniquement).


## Solution

Étendre `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` afin que la variable `afterImportSource` exclut l’importateur personnalisé.

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

Où `ENTITY_CODE` est la valeur utilisée pour le paramètre de nom d’entité dans la variable `import.xml` pour l’importateur personnalisé.

## Lecture connexe

[Configurer [!DNL cron] jobs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) dans le guide de configuration des opérations Adobe Commerce.
