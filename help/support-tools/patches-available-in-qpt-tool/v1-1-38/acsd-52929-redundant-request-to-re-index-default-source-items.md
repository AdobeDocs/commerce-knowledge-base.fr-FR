---
title: "ACSD-52929 : requête redondante pour réindexer les éléments source par défaut"
description: Appliquez le correctif ACSD-52929 pour résoudre le problème Adobe Commerce en raison duquel une requête redondante est envoyée pour réindexer les éléments source par défaut lorsque l’indexeur d’inventaire est configuré en mode asynchrone.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 978fe0d0-3917-4ba2-94bb-01c607a825cc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-52929 : requête redondante pour réindexer les éléments source par défaut

Le correctif ACSD-52929 corrige le problème en raison duquel il existe une redondance de requêtes de réindexation des éléments source par défaut lorsque l’indexeur d’inventaire est configuré en mode asynchrone. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.38 est installé. L’ID de correctif est ACSD-52929. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Il existe une redondance de requêtes pour réindexer les éléments source par défaut lorsque l’indexeur d’inventaire est configuré en mode asynchrone.

<u>Étapes à reproduire</u> :

1. Configurez [!DNL RabbitMQ].
1. Activez la stratégie de réindexation asynchrone en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** et définissez **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. Créez une source d’inventaire personnalisée.
1. Connectez-vous au tableau de bord [!DNL RabbitMQ] et accédez à l’onglet Files d’attente .
1. Vérifiez la file d&#39;attente `inventory.indexer.sourceItem` et assurez-vous qu&#39;elle ne contient aucun message.
1. Ouvrez un produit simple à partir du serveur principal, ajoutez *[!UICONTROL stock only]* à la source personnalisée et enregistrez le produit.
1. Chargez la file d&#39;attente `inventory.indexer.sourceItem` dans le tableau de bord [!DNL RabbitMQ], puis vérifiez les messages.

<u>Résultats attendus</u> :

Il n’y a qu’un seul message dans la file d’attente pour la source personnalisée.

<u>Résultats réels</u> :

Deux messages s’affichent dans la file d’attente : un pour la source par défaut et un autre pour la source personnalisée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
