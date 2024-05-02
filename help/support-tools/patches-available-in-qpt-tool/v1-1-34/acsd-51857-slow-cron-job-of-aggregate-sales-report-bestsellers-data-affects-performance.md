---
title: '"ACSD-51857 : la tâche cron lente de "aggregate_sales_report_bestsellers_data" affecte les performances"'
description: Appliquez le correctif ACSD-51857 pour résoudre le problème Adobe Commerce en raison duquel la tâche cron lente "aggregate_sales_report_bestsellers_data" affecte les grandes tables de base de données "sales_order" et "sales_order_item".
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857 : Tâche cron lente de `aggregate_sales_report_bestsellers_data` affecte les performances

Le correctif ACSD-51857 corrige le problème de la tâche lente cron. `aggregate_sales_report_bestsellers_data` affecte volumineux `sales_order` et `sales_order_item` tables de base de données. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.34 est installée. L’ID de correctif est ACSD-51857. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Performances de la tâche Cron `aggregate_sales_report_bestsellers_data` est lent `sales_order` et `sales_order_item` tables de base de données.

Pour résoudre ce problème, la requête de données principale qui récupère les données du rapport a été réécrite dans un formulaire plus efficace. Elle utilise désormais une sous-requête pour déterminer le sous-ensemble de données.

Afin que la sous-requête fonctionne le plus vite possible, un nouvel index a été ajouté pour la variable `sales_order` table de base de données : `SALES_ORDER_STORE_STATE_CREATED` basé sur `store_id`, `state`, et `created_at` colonnes.

<u>Conditions préalables</u>

Assurez-vous qu’un grand nombre de commandes sont commandées quotidiennement.

<u>Étapes à reproduire</u>

1. Exécutez le `aggregate_sales_report_bestsellers_data` tâche cron.
1. Vérifiez les données à afficher dans le tableau de bord Admin, sous le **[!UICONTROL Bestsellers]** .

<u>Résultats attendus</u>:

*[!UICONTROL Quantity per source]* sous le **[!UICONTROL Configuration]** ne devrait pas être vide.

<u>Résultats réels</u>:

*[!UICONTROL Quantity per source]* sous le **[!UICONTROL Configuration]** est vide.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
