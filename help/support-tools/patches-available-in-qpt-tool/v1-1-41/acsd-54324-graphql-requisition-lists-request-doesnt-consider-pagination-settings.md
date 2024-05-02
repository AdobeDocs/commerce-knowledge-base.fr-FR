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

# ACSD-54324 : GraphQL `requisition_lists` request ne prend pas en compte les paramètres de pagination

Le correctif ACSD-54324 corrige le problème où le GraphQL `requisition_lists` ne prend pas en compte les paramètres de pagination et renvoie tous les résultats. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.41 est installée. L’ID de correctif est ACSD-54324. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

GraphQL `requisition_lists` ne prend pas en compte les paramètres de pagination et renvoie tous les résultats.

<u>Étapes à reproduire</u>:

1. Connectez-vous à l’administrateur et accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Définir *[!UICONTROL Enable Requisition List]* to *Oui*.

1. Connectez-vous à l’interface utilisateur frontale, puis accédez à **[!UICONTROL My Requisition Lists]** depuis le menu supérieur ou **[!UICONTROL My Account]** et créer plusieurs demandes d&#39;approvisionnement (exemple : 7).
1. Après avoir généré un jeton client, exécutez le GraphQL ci-dessous `requisition_lists` requête du client.

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

1. Observez que la valeur de la variable `total_count` indique 7, alors qu’il doit afficher 4.

   Le nombre d’éléments affiche également 7 lorsqu’il doit être identique à la valeur *taille de page*.

<u>Résultats attendus</u>:

* Le nombre indiqué comme *taille de page* est renvoyé sous `total_count` et non le nombre total d&#39;enregistrements.
* Le nombre d’éléments est le même que la variable *taille de page*.

<u>Résultats réels</u>:

Le nombre total d’enregistrements est renvoyé sous `total_count`, même si *taille de page* est mentionnée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
