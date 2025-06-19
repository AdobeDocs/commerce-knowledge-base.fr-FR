---
title: Les modifications apportées à la base de données ne sont pas répercutées sur le storefront
description: Cet article fournit des solutions pour éviter les retards ou les interruptions dans l’application des mises à jour des entités. Cela inclut la manière d’éviter que les tables de logs des modifications ne soient surdimensionnées et la manière de configurer  [!DNL MySQL]  déclencheurs de table.
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Les modifications apportées à la base de données ne sont pas répercutées sur le storefront

Cet article fournit des solutions pour éviter les retards ou les interruptions dans l’application des mises à jour des entités. Cela inclut la manière d’éviter que les tables de logs des modifications ne soient surdimensionnées et la manière de configurer des déclencheurs de table [!DNL MySQL].

Produits et versions concernés :

* Adobe Commerce sur les infrastructures cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

## Problème

Les modifications apportées à la base de données ne sont pas répercutées sur le storefront, ou l’application des mises à jour d’entités est considérablement retardée. Les entités susceptibles d&#39;être affectées sont les produits, les catégories, les prix, les stocks, les règles de catalogue, les règles de vente et les règles de cible.

## Cause

Si vos indexeurs sont [configurés pour effectuer une mise à jour par planning](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers), le problème peut être dû au fait qu&#39;une ou plusieurs tables avec des journaux de modifications trop volumineux ou que des déclencheurs MySQL ne sont pas configurés.

### Tables de logs des modifications surdimensionnées

Les tables de journaux des modifications deviennent si volumineuses si la tâche `indexer_update_all_views` cron n’est pas terminée avec succès à plusieurs reprises.

Les tables de logs des modifications sont les tables de la base de données dans lesquelles les modifications apportées aux entités sont suivies. Un enregistrement est stocké dans une table des logs des modifications tant que la modification n&#39;est pas appliquée, ce qui est effectué par la tâche cron `indexer_update_all_views`. Une base de données Adobe Commerce contient plusieurs tables de logs des modifications. Elles sont nommées selon le modèle suivant : INDEXER\_TABLE\_NAME + &#39;\_cl&#39;, par exemple `catalog_category_product_cl`, `catalog_product_category_cl`. Pour plus d’informations sur le suivi des modifications dans la base de données, consultez l’article [Présentation de l’indexation > Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) dans la documentation destinée aux développeurs et développeuses.

### Déclencheurs de base de données [!DNL MySQL] non configurés

Il est probable que les déclencheurs de base de données ne soient pas configurés si, après l&#39;ajout ou la modification d&#39;une entité (produit, catégorie, règle cible, etc.), aucun enregistrement n&#39;est ajouté à la table des logs de modifications correspondante.

## Solution

>[!WARNING]
>
>Nous vous recommandons vivement de créer une sauvegarde de la base de données avant d’effectuer toute manipulation et de les éviter pendant les périodes de charge élevée du site.

### Éviter que les tables de logs des modifications ne soient surdimensionnées

Assurez-vous que la tâche cron `indexer_update_all_views` est toujours terminée avec succès.

Vous pouvez utiliser la requête SQL suivante pour obtenir toutes les instances ayant échoué de la tâche cron `indexer_update_all_views` :

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

Vous pouvez également vérifier son statut dans les journaux en recherchant les entrées `indexer_update_all_views` :

* `<install_directory>/var/log/cron.log` - pour les versions 2.3.1 et 2.2.8 et ultérieures
* `<install_directory>/var/log/system.log` - pour les versions antérieures

### Réinitialiser les déclencheurs de table [!DNL MySQL]

Pour configurer les déclencheurs de table [!DNL MySQL] manquants, vous devez redéfinir le mode de l’indexeur :

1. Basculez sur « On Save » (Lors de l’enregistrement).
1. Revenez à « Selon le calendrier ».

Utilisez la commande suivante pour effectuer cette opération.

>[!WARNING]
>
>Avant de changer de mode d’indexation, nous vous recommandons de placer votre site web en mode [maintenance](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html?lang=fr#maintenance-mode) et de [désactiver les tâches cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=fr#disable-cron-jobs) pour éviter les verrous de base de données.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>Les déclencheurs de base de données liés aux indexeurs sont ajoutés lorsque le mode d’indexeur est défini sur planifier et supprimés lorsque le mode d’indexeur est défini sur temps réel. Si les déclencheurs sont absents de votre base de données alors que les indexeurs sont définis pour la planification, définissez-les en temps réel, puis redéfinissez-les pour la planification. Cette opération réinitialise les déclencheurs.

## Lecture connexe

* [[!DNL MySQL] les tableaux sont trop volumineux](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26945) dans notre base de connaissances de support
* [Indexation : [!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) dans notre documentation destinée aux développeurs
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
