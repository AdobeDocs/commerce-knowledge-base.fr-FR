---
title: "ACSD-53098 : les produits du catalogue partagé ne reflètent pas sur l’interface frontale"
description: Appliquez le correctif ACSD-53098 pour résoudre le problème Adobe Commerce en raison duquel les produits affectés à un catalogue partagé ne se reflètent pas sur l’interface lors de l’exécution d’un index partiel.
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
exl-id: 19c66a3a-04b2-48ee-aff3-ad2b592ff876
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-53098 : les produits du catalogue partagé ne reflètent pas sur l’interface frontale

Le correctif ACSD-53098 corrige le problème en raison duquel les produits affectés à un catalogue partagé ne reflètent pas sur l’interface lors de l’exécution d’un index partiel. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.38 est installé. L’ID de correctif est ACSD-53098. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits affectés à un catalogue partagé via l’API ne s’affichent pas sur le front-end après l’exécution de la tâche cron par l’indexeur partiel, suivi du cron du consommateur.

<u>Étapes à reproduire</u> :

1. Configurez [!DNL RabbitMQ] comme service de file d’attente.
1. Passez les indexeurs en mode **[!UICONTROL Update on Schedule]**.
1. Créez un catalogue partagé et affectez-le à une entreprise.
1. Créez un produit simple et affectez-le à une catégorie. Exécutez la réindexation partielle :

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Utilisez la requête d’API suivante pour affecter le produit créé au catalogue partagé.

   ```
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Exécutez le cron suivant pour effacer les files d’attente, puis exécutez la réindexation partielle :

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Connectez-vous au front-end en tant qu’utilisateur de l’entreprise.
1. Consultez la page de catégorie de front-end.

<u>Résultats attendus</u> :

Les produits nouvellement attribués apparaissent sur le front-end.

<u>Résultats réels</u> :

Les produits nouvellement attribués n’apparaissent pas sur le front-end.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
