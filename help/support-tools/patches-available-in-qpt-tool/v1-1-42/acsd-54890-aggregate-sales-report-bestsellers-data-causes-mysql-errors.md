---
title: 'ACSD-54890: &grave;aggregate_sales_report_bestsellers_data&grave; provoque [!DNL MySQL] errors'
description: Appliquez le correctif ACSD-54890 pour résoudre le problème Adobe Commerce où "aggregate_sales_report_bestsellers_data" provoque des erreurs [!DNL MySQL] dues à une panne d’espace disque.
feature: Attributes
role: Admin, Developer
exl-id: 21a675dc-0750-4dc6-8cce-33e301f601bd
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-54890 : `aggregate_sales_report_bestsellers_data` provoque des erreurs MySQL

Le correctif ACSD-54890 corrige le problème en raison duquel `aggregate_sales_report_bestsellers_data` provoque des erreurs [!DNL MySQL] en raison d’une insuffisance d’espace disque de `/tmpdisk`. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 est installé. L’ID de correctif est ACSD-54890. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`aggregate_sales_report_bestsellers_data` provoque des erreurs **[!DNL MySQL]** en raison d’un manque d’espace `/tmpdisk`.

<u>Étapes à reproduire</u> :

Exécutez la tâche cron `aggregate_sales_report_bestsellers_data` lorsque la table `sales_bestsellers_aggregated_daily` contient une énorme quantité d&#39;enregistrements, comme des dizaines de millions d&#39;enregistrements.

<u>Résultats attendus</u> :

Aucune erreur ne se produit.

<u>Résultats réels</u> :

L’erreur suivante se produit :
`report.ERROR: Cron Job aggregate_sales_report_bestsellers_data has an error: SQLSTATE[HY000]: General error: 3 Error writing file '/tmp/#sql/fd=72' (Errcode: 28 "No space left on device")`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
