---
title: Résolution des problèmes liés au module [!UICONTROL Product Recommendations] dans Adobe Commerce
description: Cet article contient des suggestions de dépannage pour le module [!UICONTROL Product Recommendations] dans Adobe Commerce.
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Résolution des problèmes liés au module [!UICONTROL Product Recommendations] dans Adobe Commerce

Cet article aborde les suggestions de dépannage pour le

```php
magento/product-recommendations
```

module et sa dépendance

```php
saas-export
```

, car vous avez besoin que les deux modules fonctionnent pour utiliser l’outil [!UICONTROL Product Recommendations] dans Adobe Commerce.

## Produits et versions concernés

* Adobe Commerce 2.4.4 - 2.4.7

## Résolution des problèmes liés au module de recommandations de produits

Si vous avez configuré

```php
magento/product-recommendations
```

module correctement, (Vérifiez [[!UICONTROL Product Recommendations - Install and Configure]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) dans notre documentation pour les développeurs.) mais vous ne voyez aucune recommandation, essayez ce qui suit :

* Il est possible que le module n&#39;ait pas eu suffisamment de temps pour collecter des données comportementales. Laissez le système s’exécuter pendant 24 heures afin qu’il puisse commencer à collecter des données. Envisagez de déployer un type de recommandation qui ne nécessite aucune donnée comportementale, comme « *Plus comme ceci* ».

* Si les recommandations que vous avez configurées ne s’affichent pas, il est possible qu’il n’y ait pas encore suffisamment de données pour créer des recommandations pour l’utilisateur.

* Assurez-vous que l’espace de données [!DNL SaaS] ou la clé [!DNL API] sont valides. Si vous obtenez une erreur après avoir spécifié votre espace de données [!DNL SaaS] ou votre clé [!DNL API] lors de l’initialisation des recommandations de produit, vérifiez que vous avez saisi correctement les [[!DNL SaaS] espace de données et [!DNL API] clé](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) (dans notre guide d’utilisation). Pour que la clé [!DNL MageID] et la clé [!DNL API] soient liées, l’utilisateur propriétaire de la [!DNL MageID], généralement celui qui détient la licence Adobe Commerce, doit être le même utilisateur que celui qui génère la clé [!DNL API]. Si vous devez modifier le [!DNL MageID] utilisé, [envoyez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).

>[!NOTE]
>
>Si [**[!UICONTROL Cookie Restriction Mode]**](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law) (dans notre guide d’utilisation) est *activé*, Adobe Commerce ne collecte pas de données comportementales tant que l’acheteur n’a pas donné son consentement. Si **[!UICONTROL Cookie Restriction Mode]**&#x200B;est *désactivé*, Adobe Commerce collecte des données comportementales par défaut.

## Module d’exportation de [!DNL SaaS] de catalogue

Pour les problèmes liés à l’exportation de [!DNL SaaS] de catalogue (

```php
saas-export
```

) module :

1. Vérifiez que les tâches [[!DNL cron]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) (dans notre documentation destinée aux développeurs) sont en cours d’exécution.
1. Vérifiez que les [[!UICONTROL indexers]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) (dans notre documentation destinée aux développeurs) sont en cours d’exécution et le    ```php    Product Feed    ```    [!UICONTROL indexer] est défini sur    ```php    Update by Schedule    ```    .
1. Vérifiez que les modules sont *activés*. Le    ```php    saas-export    ```    metapackage installe les modules suivants, qui doivent tous être *activés* :    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Vérifiez les [logs](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging) (dans notre documentation destinée aux développeurs). Vérifiez qu’aucune erreur n’est associée aux modules ci-dessus.
1. Actualisez la [!UICONTROL Configuration cache]. Accédez à **Système** > **Outils** > **Gestion du cache**, puis effacez le [!UICONTROL Configuration cache].
1. Vérifiez que la table de base de données `cde_products_products_feed` contient des données.

   >[!NOTE]
   >
   >Si vous ne trouvez pas cette table, vérifiez la table `catalog_data_exporter_products`. Le nom de la table a été modifié dans la version 103.3.0 de [!DNL Data Export].

## Événements

[Vérifier la collecte d’événements](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/verify), dans notre documentation destinée aux développeurs, décrit les événements comportementaux envoyés à Adobe Commerce.

## Lecture connexe

* [Développement de l’administrateur des recommandations de produits](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview) dans notre documentation destinée aux développeurs
* [Présentation des recommandations de produit](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview) dans le Guide de recommandations de produit
* [Créer des recommandations de produit](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/admin/create) dans le Guide de recommandations de produit
* [Consulter les journaux et résoudre les problèmes](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) dans le Guide d’exportation des données [!DNL SaaS]
* [[!DNL SaaS] Notes de mise à jour de l’extension Data Export](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes) dans le Guide d’exportation de données Adobe Commerce pour [!DNL SaaS] Services
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook

