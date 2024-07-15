---
title: "ACSD-54324 : la demande GraphQL request_lists ne prend pas en compte les paramètres de pagination"
description: Appliquez le correctif ACSD-54324 pour résoudre le problème Adobe Commerce en raison duquel la requête "réquisition_lists" de GraphQL ne prend pas en compte les paramètres de pagination et renvoie tous les résultats.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 85297eae-bedf-4624-9758-0b68452d131b
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-54324 : la requête GraphQL `requisition_lists` ne prend pas en compte les paramètres de pagination

Le correctif ACSD-54324 corrige le problème où la requête GraphQL `requisition_lists` ne prend pas en compte les paramètres de pagination et renvoie tous les résultats. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.41 est installé. L’ID de correctif est ACSD-54324. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête GraphQL `requisition_lists` ne prend pas en compte les paramètres de pagination et renvoie tous les résultats.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur et accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Définissez *[!UICONTROL Enable Requisition List]* sur *Yes*.

1. Connectez-vous à l’interface utilisateur frontale, accédez à **[!UICONTROL My Requisition Lists]** à partir du menu supérieur ou à partir de **[!UICONTROL My Account]** et créez plusieurs demandes d’approvisionnement (par exemple : 7).
1. Après avoir généré un jeton client, exécutez la requête GraphQL `requisition_lists` ci-dessous pour le client.

   * Assurez-vous que la taille de la page est inférieure au nombre total de listes de demandes créées par vous (par exemple : 4)

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. Notez que la valeur du champ `total_count` indique 7, alors qu’elle doit afficher 4.

   Le nombre d’éléments affiche également 7 lorsqu’il doit être identique à la *taille de page*.

<u>Résultats attendus</u> :

* Le nombre répertorié comme *taille de page* est renvoyé sous `total_count` et non le nombre total d’enregistrements.
* Le nombre d’éléments est le même que la *taille de page*.

<u>Résultats réels</u> :

Le nombre total d’enregistrements est renvoyé sous `total_count`, même si la *taille de page* est mentionnée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
