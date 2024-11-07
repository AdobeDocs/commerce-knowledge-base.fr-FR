---
title: Les modifications apportées à la base de données ne sont pas répercutées sur le storefront.
description: Cet article fournit des solutions pour éviter les retards ou les interruptions dans l’application des mises à jour des entités. Cela inclut la manière d’éviter que les tables de logs ne soient surdimensionnées et la façon de configurer les déclencheurs de table  [!DNL MySQL] .
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Les modifications apportées à la base de données ne sont pas répercutées sur le storefront.

Cet article fournit des solutions pour éviter les retards ou les interruptions dans l’application des mises à jour des entités. Cela inclut la manière d’éviter que les tables de logs ne soient surdimensionnées et la configuration des déclencheurs de table [!DNL MySQL].

Produits et versions concernés :

* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

## Problème

Les modifications que vous effectuez dans la base de données ne sont pas répercutées sur le storefront, ou l’application des mises à jour des entités est considérablement retardée. Les entités susceptibles d’être affectées sont les produits, les catégories, les prix, l’inventaire, les règles de catalogue, les règles de vente et les règles de ciblage.

## Cause

Si vos indexeurs sont [ configurés pour une mise à jour par planning](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers), le problème peut être dû à une ou plusieurs tables dont les logs de modification sont trop volumineux ou à des déclencheurs MySQL non configurés.

### Tables de logs de modifications surdimensionnées

Les tables de journal des modifications deviennent aussi volumineuses si la tâche cron `indexer_update_all_views` n’est pas terminée plusieurs fois avec succès.

Les tables de journal des modifications sont les tables de base de données dans lesquelles les modifications apportées aux entités sont suivies. Un enregistrement est stocké dans une table de journal des modifications tant que la modification n’est pas appliquée, ce qui est effectué par la tâche cron `indexer_update_all_views`. Il existe plusieurs tables de journal des modifications dans une base de données Adobe Commerce. Elles sont nommées selon le modèle suivant : INDEXER\_TABLE\_NAME + &#39;\_cl&#39;, par exemple `catalog_category_product_cl`, `catalog_product_category_cl`. Vous trouverez plus d’informations sur le suivi des modifications dans la base de données dans l’article [Présentation de l’indexation > Aperçu](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) de notre documentation destinée aux développeurs.

### [!DNL MySQL] déclencheurs de base de données non configurés

Vous pensez que les déclencheurs de base de données ne sont pas configurés si, après l’ajout ou la modification d’une entité (produit, catégorie, règle de ciblage, etc.), aucun enregistrement n’est ajouté à la table du journal des modifications correspondante.

## Solution

>[!WARNING]
>
>Il est vivement recommandé de créer une sauvegarde de la base de données avant toute manipulation, et de les éviter lors de périodes de chargement importantes du site.

### Éviter que les tables de journal ne soient surchargées

Assurez-vous que la tâche cron `indexer_update_all_views` est toujours terminée.

Vous pouvez utiliser la requête SQL suivante pour obtenir toutes les instances ayant échoué de la tâche cron `indexer_update_all_views` :

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

Vous pouvez également vérifier son état dans les journaux en recherchant les entrées `indexer_update_all_views` :

* `<install_directory>/var/log/cron.log` - pour les versions 2.3.1+ et 2.2.8+
* `<install_directory>/var/log/system.log` - pour les versions antérieures

### Réinitialiser les déclencheurs de table [!DNL MySQL]

Pour configurer les déclencheurs de table [!DNL MySQL] manquants, vous devez redéfinir le mode indexeur :

1. Basculez vers &quot;Activé à l’enregistrement&quot;.
1. Revenez à &quot;En programmation&quot;.

Utilisez la commande suivante pour effectuer cette opération.

>[!WARNING]
>
>Avant de passer en mode indexeur, nous vous recommandons de mettre votre site web en mode [maintenance](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode) et [désactiver les tâches cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs) pour éviter les verrous de base de données.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>Les déclencheurs de base de données liés aux indexeurs sont ajoutés lorsque le mode indexeur est défini pour planifier et supprimer lorsque le mode indexeur est défini sur temps réel. Si les déclencheurs sont manquants dans votre base de données alors que les indexeurs sont programmés, modifiez les indexeurs en temps réel, puis redéfinissez-les sur la planification. Cela réinitialise les déclencheurs.

## Lecture connexe

* [[!DNL MySQL] les tables sont trop volumineuses](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-tables-are-too-large) dans notre base de connaissances de support
* [Indexation : [!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) dans notre documentation destinée aux développeurs
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
