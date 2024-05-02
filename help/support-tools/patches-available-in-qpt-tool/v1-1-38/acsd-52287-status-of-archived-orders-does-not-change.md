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

Le correctif ACSD-52287 corrige le problème où l’état des commandes archivées ne change pas de *terminé* to *fermée* sur grid après l’envoi de la note de crédit. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.38 est installée. L’ID de correctif est ACSD-52287. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état des commandes archivées ne change pas à partir de *terminé* to *fermée* sur grid après l’envoi de la note de crédit.

<u>Étapes à reproduire</u>:

1. Configurer *[!UICONTROL Asynchronous Indexing]*.
   * Dans la barre latérale d’administration, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Dans le panneau de gauche, développez la variable **[!UICONTROL Advanced]** et choisissez **[!UICONTROL Developer]** en-dessous.
   * Développez l’objet **[!UICONTROL Grid Settings]** .
   * Définir *[!UICONTROL Asynchronous indexing]* to *Oui*.
   * Cliquez sur **[!UICONTROL Save Config]**.
1. Configurez la variable *[!UICONTROL Order Archive]*.
   * Dans la barre latérale d’administration, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Dans le panneau de gauche, développez la variable **[!UICONTROL Sales]** et choisissez **[!UICONTROL Sales]** en-dessous.
   * Développez l’objet **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** .
   * Définir *[!UICONTROL Enable Archiving]* to *Oui* (Laissez le reste des configurations par défaut).
   * Cliquez sur **[!UICONTROL Save Config]**.
1. Placez une commande dans le front-end.
1. Exécutez la variable [!DNL cron]  pour que l’ordre apparaisse dans la variable *[!UICONTROL Admin Order Grid]*.
1. Facturer et expédier la commande pour mettre à jour l’état de la commande sur *Terminer*.
1. Exécutez la variable [!DNL cron]  pour mettre à jour la variable *[!UICONTROL Sales Order Grid]* avec le dernier état de la commande.
1. Archivez la commande.
1. Accédez au *[!UICONTROL Archived order grid]*.
1. Ouvrez la commande archivée et remboursez la commande hors ligne en créant un [!UICONTROL Credit Memo] pour que la variable [!UICONTROL Order status]: *Fermé*.
1. Exécutez la variable [!DNL cron] pour quelques fois.
1. Vérifiez les *[!UICONTROL Archived order grid]* pour le nouvel état de la commande.

<u>Résultats attendus</u>:

L’ordre s’affiche sous la forme *Fermé*.

<u>Résultats réels</u>:

L’ordre s’affiche sous la forme *Terminer*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
