---
title: 'ACSD-49179 : le rapport Commandes affiche des quantités incorrectes pour différents magasins.'
description: Appliquez le correctif ACSD-49179 pour résoudre le problème Adobe Commerce en raison duquel le rapport de commandes affiche des montants incorrects en cas de devises différentes pour différents magasins.
exl-id: 01e4cd2d-6c33-4cf5-bf31-bbc34eaaed1a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-49179 : le rapport Commandes affiche des quantités incorrectes pour différents magasins

Le correctif ACSD-49179 corrige le problème en raison duquel le rapport de commandes affiche des montants incorrects en cas de devises différentes pour différents magasins. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 est installé. L’ID de correctif est ACSD-49179. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le rapport Commandes affiche des montants incorrects en cas de devises différentes pour différents magasins.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** et définissez [!UICONTROL Catalog Price Scope] = [!UICONTROL Website].
1. Créez un site web, un magasin et une vue de magasin supplémentaires.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]** et définissez :
   * Configuration par défaut :
      * Devise de base : USD
      * Devise d’affichage par défaut : USD
      * Devises autorisées : EUR, USD et THB (thaï baht)
   * Site web principal :
      * Devise de base : EUR
      * Devise d’affichage par défaut : EUR
      * Devises autorisées : EUR
   * Nouveau site Web supplémentaire :
      * Devise de base : THB (thaï baht)
      * Devise d’affichage par défaut : THB (thaï, baht)
      * Devises autorisées : THB (thaï baht)
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]** et définissez les taux de conversion vides pour le THB (définissez les taux sur 1 000).
1. Créez un produit, attribuez-le aux deux sites web et passez une commande avec ce produit sur le site web supplémentaire précédemment créé.
1. Assurez-vous que la commande est à l&#39;état *Traitement* (facturez-la).
1. Dans le serveur principal, accédez à **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Cliquez sur l&#39;avertissement **[!UICONTROL Yellow]** pour actualiser les statistiques.
1. Définissez la portée du rapport sur le site web supplémentaire précédemment créé et définissez le filtre comme suit :
   * [!UICONTROL Date Used] : [!UICONTROL Created]
   * [!UICONTROL Period] : [!UICONTROL Day]
   * [!UICONTROL From and To] : le même jour où la commande de test a été passée
   * [!UICONTROL Order Status] : [!UICONTROL Any]
   * [!UICONTROL Empty rows] : [!UICONTROL No]
   * [!UICONTROL Show Actual Values] : [!UICONTROL No]

<u>Résultats attendus</u> :

Le total des ventes indique le montant correct converti dans la devise du site web.

<u>Résultats réels</u> :

Le total est zéro.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
