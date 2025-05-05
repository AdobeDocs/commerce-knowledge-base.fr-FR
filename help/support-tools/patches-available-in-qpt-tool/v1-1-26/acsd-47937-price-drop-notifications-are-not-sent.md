---
title: "ACSD-47937 : notifications de baisse de prix non envoyées en raison de la mise en cache au niveau de l’application"
description: Appliquez le correctif ACSD-47937 pour résoudre le problème Adobe Commerce en raison duquel les notifications de baisse de prix ne sont pas toujours envoyées en raison de la mise en cache au niveau de l’application.
exl-id: f39c9ef6-4689-427f-bd61-3a52dec88be2
feature: Admin Workspace, Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-47937 : notification de baisse de prix non envoyée en raison de la mise en cache au niveau de l’application

Le correctif ACSD-47937 corrige le problème en raison duquel les notifications de baisse de prix ne sont pas toujours envoyées en raison de la mise en cache au niveau de l’application. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 est installé. L’ID de correctif est ACSD-47937. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 et 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4, 2.4.5 et 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients n’obtiennent pas d’e-mail de baisse de prix de produit pour les changements de prix de produit ultérieurs.

<u>Étapes à reproduire</u> :

1. Activez **[!UICONTROL Product Alert]** pour *[!UICONTROL Price Changes]* et *[!UICONTROL Back in Stock]* dans **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. Activez **[!UICONTROL Display Out of Stock Products]**.
1. Créez un produit simple (ABC) avec une quantité = 0.
1. Créez un client à partir du storefront et abonnez-vous au produit ci-dessus pour obtenir des alertes de produits pour les baisses de prix.
1. Démarrez l’alerte de produit pour les clients.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Déposez le prix du produit ABC.
1. Déclenchez le cron d’alerte du produit.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Déposez à nouveau le prix du produit ABC.
1. Déclenchez le cron d’alerte du produit.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Si vous ne connaissez pas l&#39;outil [!DNL n98], vous pouvez exécuter `bin/magento cron:run command` comme d&#39;habitude et surveiller la table `cron_schedule` pour vous assurer que la tâche `catalog_product_alert` obtient l&#39;état de réussite.

<u>Résultats attendus</u> :

Le deuxième email de baisse de prix est envoyé.

<u>Résultats réels</u> :

Le deuxième email de baisse de prix n&#39;est pas envoyé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
