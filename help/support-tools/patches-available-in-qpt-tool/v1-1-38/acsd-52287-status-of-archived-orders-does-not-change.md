---
title: "ACSD-52287 : L’état des commandes archivées ne change pas"
description: Appliquez le correctif ACSD-52287 pour résoudre le problème Adobe Commerce en raison duquel l’état des commandes archivées ne passe pas de *terminé* à *fermé* sur la grille après l’envoi de la note de crédit.
feature: Orders, Checkout
role: Admin, Developer
exl-id: c88c5c87-eec7-4105-9e4e-815d0888a34b
source-git-commit: 178023177975f210ebf7dd07e8c75cfe3ac89ff1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-52287 : L’état des commandes archivées ne change pas

Le correctif ACSD-52287 corrige le problème où l’état des commandes archivées ne passe pas de *completed* à *closed* sur la grille après l’envoi de la note de crédit. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 est installé. L’ID de correctif est ACSD-52287. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état des commandes archivées ne passe pas de *completed* à *closed* sur la grille après l’envoi de la note de crédit.

<u>Étapes à reproduire</u> :

1. Configurez *[!UICONTROL Asynchronous Indexing]*.
   * Dans la barre latérale Admin, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Dans le panneau de gauche, développez la section **[!UICONTROL Advanced]** et choisissez **[!UICONTROL Developer]** en dessous.
   * Développez la section **[!UICONTROL Grid Settings]** .
   * Définissez *[!UICONTROL Asynchronous indexing]* sur *Yes*.
   * Cliquez sur **[!UICONTROL Save Config]**.
1. Configurez le *[!UICONTROL Order Archive]*.
   * Dans la barre latérale Admin, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Dans le panneau de gauche, développez la section **[!UICONTROL Sales]** et choisissez **[!UICONTROL Sales]** en dessous.
   * Développez la section **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** .
   * Définissez *[!UICONTROL Enable Archiving]* sur *Oui* (laissez le reste des configurations par défaut).
   * Cliquez sur **[!UICONTROL Save Config]**.
1. Placez une commande dans le front-end.
1. Exécutez le [!DNL cron] pour que l’ordre d’affichage s’affiche dans le *[!UICONTROL Admin Order Grid]*.
1. Facturez et expédiez la commande pour mettre à jour l’état de la commande sur *Complete*.
1. Exécutez le [!DNL cron] pour mettre à jour le *[!UICONTROL Sales Order Grid]* avec le dernier état de commande.
1. Archivez la commande.
1. Accédez au *[!UICONTROL Archived order grid]*.
1. Ouvrez la commande archivée et remboursez la commande hors ligne en créant un [!UICONTROL Credit Memo] pour effectuer le [!UICONTROL Order status] : *Fermé*.
1. Exécutez le [!DNL cron] plusieurs fois.
1. Vérifiez le *[!UICONTROL Archived order grid]* pour connaître le nouvel état de la commande.

<u>Résultats attendus</u> :

La commande s’affiche sous la forme *Fermée*.

<u>Résultats réels</u> :

La commande s’affiche sous la forme *Complete*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
