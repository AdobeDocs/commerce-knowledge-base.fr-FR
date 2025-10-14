---
title: Résolution des problèmes liés au module [!UICONTROL Product Recommendations] dans Adobe Commerce
description: Cet article décrit les suggestions de dépannage pour le module [!UICONTROL Product Recommendations] dans Adobe Commerce.
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Résolution des problèmes liés au module [!UICONTROL Product Recommendations] dans Adobe Commerce

Cet article présente les suggestions de dépannage pour la

```php
magento/product-recommendations
```

module et sa dépendance

```php
saas-export
```

car vous avez besoin que les deux modules fonctionnent afin d’utiliser l’outil [!UICONTROL Product Recommendations] dans Adobe Commerce.

## Produits et versions concernés

* Adobe Commerce 2.4.4 - 2.4.7

## Dépannage du module de recommandations de produits

Si vous avez configuré la variable

```php
magento/product-recommendations
```

module correctement (consultez [[!UICONTROL Product Recommendations - Install and Configure]](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) dans notre documentation destinée aux développeurs.) mais vous ne voyez aucune recommandation, essayez les méthodes suivantes :

* Il est possible que le module n’ait pas eu assez de temps pour collecter des données comportementales. Permet au système de fonctionner pendant 24 heures afin de pouvoir commencer à collecter des données. Envisagez de déployer un type de recommandation qui ne nécessite aucune donnée comportementale, telle que &quot;*Plus comme ceci*&quot;.

* Si vous ne voyez pas les recommandations que vous avez configurées, il est possible qu’il n’y ait pas encore suffisamment de données pour créer des recommandations pour l’utilisateur.

* Assurez-vous que l’espace de données [!DNL SaaS] ou la clé [!DNL API] sont valides. Si vous obtenez une erreur après avoir spécifié votre espace de données [!DNL SaaS] ou votre clé [!DNL API] lors de l’initialisation des recommandations de produits, vérifiez que vous avez correctement saisi l’[[!DNL SaaS] espace de données et la  [!DNL API] clé](https://experienceleague.adobe.com/fr/docs/commerce-admin/config/services/saas) (dans notre guide d’utilisation). Pour garantir que les clés [!DNL MageID] et [!DNL API] sont liées, l’utilisateur propriétaire de [!DNL MageID], généralement l’utilisateur propriétaire de la licence Adobe Commerce, doit être le même utilisateur qui génère la clé [!DNL API]. Si vous devez modifier le [!DNL MageID] utilisé, [soumettez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Si [**[!UICONTROL Cookie Restriction Mode]**](https://experienceleague.adobe.com/fr/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law) (dans notre guide de l’utilisateur) est *activé*, Adobe Commerce ne collecte pas de données comportementales tant que le client n’a pas donné son consentement. Si **[!UICONTROL Cookie Restriction Mode]**&#x200B;est *désactivé*, Adobe Commerce collecte les données comportementales par défaut.

## Module d&#39;export de catalogue [!DNL SaaS]

Pour les problèmes liés à l’exportation du catalogue [!DNL SaaS] (

```php
saas-export
```

) :

1. Vérifiez que les tâches [[!DNL cron]](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) (dans la documentation destinée aux développeurs) sont en cours d’exécution.
1. Vérifiez que les [[!UICONTROL indexers]](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/manage-indexers) (dans notre documentation destinée aux développeurs) sont en cours d’exécution et que la variable    ```php    Product Feed    ```    [!UICONTROL indexer] est défini sur    ```php    Update by Schedule    ```    .
1. Vérifiez que les modules sont *enabled*. La variable    ```php    saas-export    ```    metapackage installe les modules suivants, qui doivent tous être *enabled* :    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Consultez les [logs](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/enable-logging) (dans notre documentation destinée aux développeurs). Assurez-vous qu’aucune erreur n’est associée aux modules ci-dessus.
1. Actualisez le [!UICONTROL Configuration cache]. Accédez à **System** > **Tools** > **Cache Management**, puis effacez le [!UICONTROL Configuration cache].
1. Vérifiez qu’il y a des données dans la table de base de données `cde_products_products_feed`.

   >[!NOTE]
   >
   >Si vous ne trouvez pas cette table, vérifiez la table `catalog_data_exporter_products`. Le nom de la table a été modifié dans la version 103.3.0 de [!DNL Data Export].

## Événements

[Vérifier la collecte des événements](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/product-recommendations/getting-started/verify), dans notre documentation destinée aux développeurs, décrit les événements comportementaux envoyés à Adobe Commerce.

## Lecture connexe

* [Développement de l’administrateur Recommendations du produit](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/product-recommendations/developer/development-overview) dans notre documentation destinée aux développeurs
* [Présentation du Recommendations du produit](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/product-recommendations/overview) dans le guide de Recommendations du produit
* [Créer un Recommendations de produit](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/product-recommendations/admin/create) dans le guide de Recommendations de produit
* [Consultez les journaux et dépannage](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) dans le [!DNL SaaS] Guide d’exportation de données
* [[!DNL SaaS] Notes de mise à jour de l’extension d’exportation de données](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/saas-data-export/release-notes) dans le guide d’exportation de données Adobe Commerce pour les services [!DNL SaaS]
* [&#x200B; Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce

