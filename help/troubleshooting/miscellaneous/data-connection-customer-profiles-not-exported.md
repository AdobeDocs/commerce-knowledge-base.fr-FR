---
title: Les profils client n’apparaissent pas dans Experience Platform
description: Cet article fournit des étapes de dépannage si les données de votre profil client n’apparaissent pas dans Experience Platform lors de l’utilisation de l’extension  [!DNL Data Connection] .
feature: Personalization, Integration, Configuration
role: Admin, Developer
exl-id: 4f12b032-0bee-47da-927a-8d4c2d8b8276
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# Les profils client n’apparaissent pas dans Experience Platform

Cet article fournit des étapes de dépannage si les données de votre profil client n’apparaissent pas dans Experience Platform lors de l’utilisation de l’extension Data Connection.

## Produits et versions concernés

* Adobe Commerce 2.4.x avec extension [!DNL Data Connection] installée

## Problème

Vous avez installé et configuré l’extension [[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) et vous avez activé l’envoi des données de profil client à Experience Platform, mais ces données de profil n’apparaissent pas dans Experience Platform.

## Solution

Si les informations de profil client n’apparaissent pas dans Experience Platform, vérifiez les points suivants :

### Vérifiez que la dernière version de [!DNL Data Connection] est installée

Assurez-vous d’avoir installé la dernière version de l’extension `experience-platform-connector`.

Voir les [[!DNL Data Connection] notes de mise à jour de l’extension](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/release-notes) pour plus d’informations sur la dernière version.

>[!NOTE]
>
>La dernière version de l’extension [!DNL Data Connection] inclut le module `customers-connector`, qui est chargé d’envoyer les données de profil à Experience Platform. Le module `customers-connector` doit être de la version `1.2.0` ou supérieure.

### Vérifiez que le module customer-connector est configuré

Vérifiez que le module `customers-connector` est configuré en fonction de votre scénario d’installation.

#### Adobe Commerce sur les infrastructures cloud

1. Activez la variable globale `ENABLE_EVENTING` dans `.magento.env.yaml`. [En savoir plus](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global).

   ```bash
       stage:
           global:
               ENABLE_EVENTING: true
   ```

1. Validez et envoyez les fichiers mis à jour dans l’environnement cloud. Lorsque le déploiement est terminé, activez l’envoi d’événements avec la commande suivante :

   ```bash
       bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

#### Installation sur site d’Adobe Commerce

Exécutez les commandes suivantes afin d’activer la génération de code et les événements Adobe Commerce :

```bash
   bin/magento events:generate:module
   bin/magento module:enable Magento_AdobeCommerceEvents
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Confirmez que vous avez activé la capture des données de profil et leur envoi à Experience Platform

Dans Commerce Admin, vérifiez que les champs suivants sont définis :

* Dans **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Data Connection]**, vérifiez que les cases à cocher [!UICONTROL Back office events] et [!UICONTROL Customer profiles] sont activées.
* Assurez-vous que le champ *[!UICONTROL Profile Dataset ID]* est correct et qu’il correspond à un jeu de données différent de celui que vous utilisez actuellement pour les données comportementales et d’événement de back-office.

### Vérifier si les événements sont acheminés vers l’évaluation ou la production

1. Exécutez la commande suivante pour afficher l&#39;environnement Adobe Developer courant :

   ```bash
   Copy code
   bin/magento config:show
   adobe_io_events/integration/adobe_io_environment
   ```

1. Si l’environnement est défini sur *[!UICONTROL Stage]*, définissez-le sur *[!UICONTROL Production]* avec la commande suivante :

   ```bash
   Copy code
   bin/magento config:set adobe_io_events/integration/adobe_io_environment
   production
   ```

### Table SaaS des données d’événement de requête

Connectez-vous et exécutez la requête [!DNL SQL] suivante pour vérifier que les enregistrements de profil client apparaissent dans le
`event_data_saas` le tableau et qu&#39;il n&#39;y a aucune erreur :

```sql
Copy code
select * from event_data_saas;
```

### Gérer les erreurs de publication d’événement

1. Si vous rencontrez l’erreur suivante, assurez-vous que les clés du sandbox et du connecteur SaaS de production sont correctes :

   ```css
   Copy code
   2024-06-07 14:37:57 | 2024-06-07 14:38:03 | 1 | 0 | Event publishing
   failed: Error code: 403; reason: Forbidden { "error": { "code":
   "Forbidden", "message": "Client ID is invalid", "details": {
   "error_code": "403003" } } }
   ```

1. Accédez à la page *[!UICONTROL Commerce Services Connector]* de l’Administration et vérifiez que les clés [!UICONTROL sandbox/production] spécifiées sont correctement configurées. Vérifiez également que les paramètres de [!UICONTROL sandbox/production] du compte Commerce correspondent à ceux affichés dans le [!UICONTROL Commerce Services Connector]. En savoir [plus](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas#apikey).

### Vérifiez si l’ID de service se trouve dans la liste autorisée et confirmez-le auprès de l’assistance Adobe Commerce

1. Vérifiez que le `serviceId` de [!UICONTROL Commerce Services Connector] apparaît dans la liste autorisée dans Adobe Commerce.
1. Contactez l’assistance technique d’Adobe Commerce [](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) pour confirmer le statut de la liste autorisée.

## Lecture connexe

* Extension [[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) dans le guide d’utilisation des services Commerce
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
