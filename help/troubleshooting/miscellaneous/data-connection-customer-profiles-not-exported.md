---
title: Profils client n’apparaissant pas dans l’Experience Platform
description: Cet article décrit les étapes de dépannage si les données de votre profil client n’apparaissent pas dans l’Experience Platform lors de l’utilisation de l’extension  [!DNL Data Connection] .
feature: Personalization, Integration, Configuration
role: Admin, Developer
source-git-commit: a520ef45f1c55dbf34a98c4f4d3ab49814535434
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Profils client n’apparaissant pas dans l’Experience Platform

Cet article décrit les étapes de dépannage si les données de profil client n’apparaissent pas dans l’Experience Platform lors de l’utilisation de l’extension Data Connection.

## Produits et versions concernés

* Adobe Commerce 2.4.x avec l’extension [!DNL Data Connection] installée

## Problème

Vous avez installé et configuré l’extension [[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) et activé l’envoi des données de profil client à l’Experience Platform, mais ces données de profil n’apparaissent pas dans l’Experience Platform.

## Solution

Si les informations de profil du client ne s’affichent pas dans l’Experience Platform, vérifiez les points suivants :

### Vérifiez que la dernière version de [!DNL Data Connection] est installée.

Vérifiez que vous avez installé la dernière version de l’extension `experience-platform-connector`.

Pour plus d’informations sur la dernière version, voir les [[!DNL Data Connection] notes de mise à jour de l’extension](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/release-notes) .

>[!NOTE]
>
>La dernière version de l’extension [!DNL Data Connection] inclut le module `customers-connector`, responsable de l’envoi des données de profil à l’Experience Platform. Le module `customers-connector` doit être de la version `1.2.0` ou supérieure.

### Vérifiez que le module customer-connector est configuré.

Vérifiez que le module `customers-connector` est configuré en fonction de votre scénario d’installation.

#### infrastructure Adobe Commerce on Cloud

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

### Confirmez que vous avez activé la capture et l’envoi des données de profil à l’Experience Platform

Dans l’administrateur Commerce, assurez-vous que les champs suivants sont définis :

* Dans **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Data Connection]**, vérifiez que les cases à cocher [!UICONTROL Back office events] et [!UICONTROL Customer profiles] sont activées.
* Assurez-vous que le champ *[!UICONTROL Profile Dataset ID]* est correct et est un jeu de données différent de celui que vous utilisez actuellement pour les données d’événement comportemental et back-office.

### Vérifier si les événements sont acheminés vers l’évaluation ou la production

1. Exécutez la commande suivante pour afficher l’environnement Adobe Developer actuel :

   ```bash
   Copy code
   bin/magento config:show
   adobe_io_events/integration/adobe_io_environment
   ```

1. Si l’environnement est défini sur *[!UICONTROL Stage]*, remplacez-le par *[!UICONTROL Production]* avec la commande suivante :

   ```bash
   Copy code
   bin/magento config:set adobe_io_events/integration/adobe_io_environment
   production
   ```

### Table SaaS des données d’événement de requête

Connectez et exécutez la requête SQL suivante pour vérifier que les enregistrements de profil client apparaissent dans le
table `event_data_saas` et qu&#39;il n&#39;y a pas d&#39;erreur :

```sql
Copy code
select * from event_data_saas;
```

### Gestion des erreurs de publication d’événement

1. Si vous rencontrez l’erreur suivante, assurez-vous que les clés de connecteur SaaS de test et de production sont correctes :

   ```css
   Copy code
   2024-06-07 14:37:57 | 2024-06-07 14:38:03 | 1 | 0 | Event publishing
   failed: Error code: 403; reason: Forbidden { "error": { "code":
   "Forbidden", "message": "Client ID is invalid", "details": {
   "error_code": "403003" } } }
   ```

1. Accédez à la page *[!UICONTROL Commerce Services Connector]* de l’administrateur et assurez-vous que les clés [!UICONTROL sandbox/production] spécifiées sont correctement configurées. Vérifiez également que les paramètres du compte Commerce [!UICONTROL sandbox/production] correspondent à ceux affichés dans [!UICONTROL Commerce Services Connector]. Découvrez [more](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas#apikey).

### Vérifiez si l’ID de service est dans la liste autorisée et confirmez avec la prise en charge d’Adobe Commerce.

1. Vérifiez que le [!UICONTROL Commerce Services Connector] `serviceId` apparaît en liste autorisée dans Adobe Commerce.
1. Contactez le [support Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) pour confirmer l’état de la liste autorisée.

## Lecture connexe

Voir l’extension [[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) dans le guide d’utilisation des services Commerce.
