---
title: "BB2B-2598 : ajoute la fonctionnalité de mise en cache à storeConfig, currency, country, countries, availableStores GraphQl requests"
description: Appliquez le correctif BB2B-2598 pour ajouter la fonctionnalité de mise en cache aux requêtes GraphQl storeConfig, currency, country, countries et availableStores.
exl-id: 37551954-d721-4f3a-b237-cd795f715a5f
feature: B2B, GraphQL, Cache
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# BB2B-2598 : ajoute la fonctionnalité de mise en cache à `storeConfig`, `currency`, `country`, `countries` et `availableStores` requêtes GraphQl

Le correctif BB2B-2598 ajoute la fonctionnalité de mise en cache aux requêtes `storeConfig`, `currency`, `country`, `countries` et `availableStores` GraphQl. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 est installé. L’ID de correctif est BB2B-2598. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7-beta1.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`availableStores`, `countries`, `country`, `currency`, `storeConfig` et `customAttributeMetadata` Les requêtes GraphQL ne peuvent pas être mises en cache.

<u>Conditions préalables</u> :

* Le serveur pointe vers le serveur principal Adobe Commerce en pointant vers [!DNL Varnish].
* Le paramètre de configuration `system/full_page_cache/caching_application` est défini sur *2* ([!DNL Varnish]) ou accédez à Administration Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > et définissez-le sur [!DNL Varnish].

Une fois le correctif appliqué, exécutez les étapes suivantes pour vous assurer que la fonctionnalité de mise en cache est désormais disponible :

1. Envoyez la requête `GET` à l’une des requêtes GraphQL répertoriées ci-dessus, à l’aide de n’importe quel champ arbitraire.
1. Renvoyer la requête sans modification ; vous remarquerez qu’elle est beaucoup plus rapide. Notez que la requête n’est pas envoyée au serveur principal, mais elle est entièrement gérée par [!DNL Varnish] en tant qu’accès au cache.
1. Si un BAT supplémentaire est requis, commentez le non-ensemble de l’en-tête `X-Magento-Debug` présent dans notre [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227), puis redémarrez [!DNL Varnish] et exécutez à nouveau les étapes ci-dessus.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
