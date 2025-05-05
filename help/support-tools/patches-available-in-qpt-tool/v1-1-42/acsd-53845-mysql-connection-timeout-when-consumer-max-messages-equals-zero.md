---
title: 'ACSD-53845 : problème de délai d’expiration de la connexion MySQL lorsque consumer max_messages = 0'
description: Appliquez le correctif ACSD-53845 pour résoudre le problème Adobe Commerce où la connexion MySQL expire lorsque le consommateur &grave;max_messages = 0&grave;.
feature: REST, Configuration
role: Admin, Developer
exl-id: 68f862ed-5401-41e9-a6cc-cef44ebc1915
source-git-commit: 6fa7182a807147a00ad750966cd839ec18ffe0c7
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ACSD-53845 : problème de délai d’expiration de la connexion MySQL lorsque le consommateur `max_messages = 0`

Le correctif ACSD-53845 corrige le problème de délai d’expiration de la connexion MySQL lorsque le consommateur `max_messages = 0`. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.42 est installé. L’ID de correctif est ACSD-53845. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La connexion MySQL expire lorsque le consommateur `max_messages = 0`.

Toutefois, la connexion à la base de données sera restaurée lors du démarrage d’une transaction.

<u>Étapes à reproduire</u> :

1. Envoyez une requête pour mettre à jour des produits en masse à l’aide du point de terminaison de l’API REST `async/bulk/V1/products`.
1. Vérifiez l’état dans la table `magento_operation`.

<u>Résultats attendus</u> :

Les produits sont mis à jour.

<u>Résultats réels</u> :

1. Une erreur est consignée :

   ```
   report.CRITICAL: Message has been rejected: SQLSTATE[HY000]: General error: 2006 MySQL server has gone away [] []
   ```

1. *status* pour cette opération reste *4* dans la table `magento_operation`.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
