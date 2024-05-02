---
title: Impossible de modifier le moteur de recherche à l’aide de l’administrateur Commerce (le menu Moteur de recherche est inaccessible)
description: Cet article fournit une solution pour modifier le moteur de recherche Adobe Commerce à l’aide de Commerce Admin si le champ Moteur de recherche n’est pas affiché ou si la case à cocher Utiliser la valeur du système est grisée et inaccessible.
exl-id: 5b0f728c-6a8d-446d-9553-5abc3d01e516
feature: Admin Workspace, Search, Variables
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Impossible de modifier le moteur de recherche à l’aide de l’administrateur Commerce (le menu Moteur de recherche est inaccessible)

>[!WARNING]
>
> [Le moteur de recherche de catalogue MySQL sera supprimé dans Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Vous devez avoir configuré et configuré l’hôte Elasticsearch avant d’installer la version 2.4.0. Voir [Installation et configuration de l’Elasticsearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html).

Cet article fournit une solution pour modifier le moteur de recherche Adobe Commerce à l’aide de Commerce Admin si la variable **Moteur de recherche** ne s’affiche pas ou le champ **Utiliser la valeur système** est grisée et inaccessible.

Dans cet article :

* [Versions affectées](#affected-versions)
* [Modification du moteur de recherche à l’aide de l’administrateur Commerce (étapes)](#change-search-engine-using-magento-admin-steps)
* [Problèmes avec Adobe Commerce sur site)](#magento-commerce-on-premise)
* [Adobe Commerce sur l’infrastructure cloud](#magento-commerce-cloud)

## Versions affectées

* Adobe Commerce sur site : 2.X.X
* Adobe Commerce sur l’infrastructure cloud :
   * Version : 2.X.X
   * Architecture de la formule de départ et de la formule Pro
* MySQL, Elasticsearch : toutes les versions prises en charge

## Modification du moteur de recherche à l’aide de l’administrateur (étapes)

1. Connectez-vous à l’administrateur en tant qu’administrateur.
1. Dans la barre latérale d’administration gauche, cliquez sur **Magasins**. Ensuite, sous **Paramètres**, choisissez **Configuration**.
1. Dans le panneau de gauche, sous **Catalogue,** select **Catalogue**.
1. Développez l’objet **Recherche catalogue** .    ![catalog_menu.png](assets/catalog_menu.png)
1. Accédez au **Moteur de recherche** et supprimer la sélection de la propriété **Utiliser la valeur système** .
1. Cliquez sur le bouton **Moteur de recherche** et sélectionnez l’une des options disponibles.    ![search_engine_menu.png](assets/search_engine_menu.png)
1. Cliquez sur **Enregistrer la configuration** dans le coin supérieur droit de la page.

## Problèmes avec Adobe Commerce sur site

### Problème 1 : le champ Moteur de recherche ne s’affiche pas

Lorsque vous accédez à la variable **Recherche catalogue** , **Moteur de recherche** ne s’affiche pas du tout.

![search_engine_not_displayed.png](assets/search_engine_not_displayed.png)

### Cause : le mode Boutique n’est pas la configuration par défaut

La vue du magasin pour l’administrateur a été définie sur n’importe quelle valeur autre que *Configuration par défaut*.

Le moteur de recherche est un jeu de configuration global au niveau de l’application, et non sur la portée du magasin. Les magasins d’une application Adobe Commerce ne peuvent pas utiliser des moteurs de recherche différents.

### Solution : définissez la vue du magasin sur la configuration par défaut

1. Connectez-vous à l’administrateur en tant qu’administrateur.
1. Dans la barre latérale d’administration gauche, cliquez sur **Magasins**. Ensuite, sous **Paramètres**, choisissez **Configuration**.
1. Dans le coin supérieur gauche, cliquez sur le bouton **Affichage en magasin** sélecteur et choisissez *Configuration par défaut*.
1. Cliquez sur **OK** dans la boîte de dialogue de confirmation pour approuver la modification de la vue de magasin.

![change_store_view.png](assets/change_store_view.png)

**Documentation connexe :** [Modification de la portée](https://experienceleague.adobe.com/docs/commerce-admin/config/scope-change.html#set-the-scope) dans notre guide d’utilisation.

### Problème 2 : impossible de décocher &quot;Utiliser la valeur système&quot;

Lorsque vous accédez à la variable **Recherche catalogue** de la section Admin, la section **Utiliser la valeur système** est grisée. vous ne pouvez donc pas supprimer la sélection de la case à cocher pour modifier ultérieurement le moteur de recherche.

### Cause

Le moteur de recherche par défaut a été configuré au niveau de la configuration de l’application dans la variable `app/etc/env.php` ou `app/etc/config.php` ne peuvent donc pas être modifiés à l’aide de l’administrateur.

Exemple de section avec configuration par défaut du moteur de recherche :

```php
'system'=>
array (
'default'=>
array (
'catalog'=>
array (
'search'=>
array (
'engine'=>'mysql',
),
),
),
),
```

### Solution

Supprimez la section avec la configuration par défaut du moteur de recherche de la `app/etc/env.php` ou le `app/etc/config.php` fichiers de configuration.

### Articles connexes dans notre documentation destinée aux développeurs

[Fichiers de configuration Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/files/deployment-files.html) dans le guide de configuration d’Adobe Commerce

## Adobe Commerce sur l’infrastructure cloud

Le fait de changer de moteur de recherche à l’aide de l’option Administration n’est pas disponible dans Adobe Commerce sur l’infrastructure cloud en raison de l’organisation de l’infrastructure cloud.

Au cours du processus de déploiement, les scripts de déploiement d’Adobe Commerce on Cloud Infrastructure vérifient si l’Elasticsearch a été déclaré dans la variable `MAGENTO_CLOUD_RELATIONSHIPS` Variable . S’il est déclaré, l’Elasticsearch est sélectionné en tant que moteur de recherche actif et configuré automatiquement ; la variable [Moteur de recherche MySQL](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) devient inaccessible dans l’administrateur. Si la relation Elasticsearch n’a pas été déclarée, MySQL est défini sur actif et Elasticsearch devient inaccessible.

Il est déconseillé de modifier la variable `app/etc/env.php` ou le `app/etc/config.php` fichiers de configuration directement sur votre environnement cloud ; c’est pourquoi la modification de ces fichiers pour que le moteur Elasticsearch s’affiche dans l’Admin (la solution recommandée dans la section précédente) ne s’applique pas à votre projet cloud.

### Modification du moteur de recherche dans les environnements d’évaluation et de production

Avant de passer du moteur de recherche MySQL à l’Elasticsearch dans vos environnements d’évaluation et de production, assurez-vous que vous avez déjà [envoi d’un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demande d’activation d’Elasticsearch sur l’environnement et le ticket a été résolu.

Pour modifier le moteur de recherche utilisé dans vos environnements d’évaluation et de production, modifiez la variable `SEARCH_CONFIGURATION` de la variable d’environnement `.magento.env.yaml` sur votre environnement local, puis transférez les modifications vers les environnements d’intégration et d’évaluation/de production pour que les modifications soient prises en compte.

Si vous passez de MySQL à Elasticsearch, la variable SEARCH\_CONFIGURATION du résultat `.magento.env.yaml` peut se présenter comme suit :

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: elasticsearch
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '123456'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

### Documentation connexe

#### Base de connaissances d’assistance

* [Activation d’Elasticsearch dans le cloud](/help/how-to/general/enable-elasticsearch-on-cloud.md)

#### Documentation destinée aux développeurs

* [Configuration du service Elasticsearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html)
* [Créer et déployer](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) (documentation sur la fonction `.magento.env.yaml` fichier de configuration)
* [Déploiement de variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) ([Section SEARCH\_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#search_configuration))
* [Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) (documentation sur la fonction `.magento/services.yaml` fichier de configuration)
