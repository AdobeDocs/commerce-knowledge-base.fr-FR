---
title: "ACSD-47910 : commandes, factures, envois, notes de crédit manquants dans les grilles d’entités respectives"
description: Appliquez le correctif ACSD-47910 pour résoudre le problème Adobe Commerce en raison duquel il manque des commandes, des factures, des envois et des avoirs dans les grilles d’entités respectives.
exl-id: 4eb897ec-16e4-420e-89a6-c8f7c8740303
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-47910 : commandes, factures, envois et notes de crédit manquants dans les grilles d’entités respectives

Le correctif ACSD-47910 corrige le problème en raison duquel il manque des commandes, des factures, des envois et des notes de crédit dans les grilles d’entités respectives. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.25 est installée. L’ID de correctif est ACSD-47910. La version dans laquelle ce problème sera corrigé n’est pas encore disponible.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Commandes, factures, envois et notes de crédit manquants dans les grilles de chaque entité.

<u>Étapes à reproduire</u>:

1. Activer **[!UICONTROL Asynchronous indexing]** at **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. Placez deux commandes.
1. Exécutez le cron pour synchroniser ces commandes avec la grille.
1. Ouvrez l’une des commandes et rendez-la prête à être facturée. N&#39;ENVOYEZ PAS ENCORE LA FACTURE.
1. Préparez une nouvelle commande à placer sur le front-end. NE CLIQUEZ PAS ENCORE SUR LE BOUTON PLACER LA COMMANDE .
1. Ajouter un `sleep(30)` dans le `foreach` at `NotSyncedDataProvider::L43`.
1. Exécuter `bin/magento cron:run`.
1. Maintenant passez le nouvel ordre.
1. Facturez la commande précédente.
1. Exécutez à nouveau le cron en attendant la synchronisation du nouvel ordre.
1. Accédez à la grille de commande dans Admin.

<u>Résultats attendus</u>:

Le nouvel ordre doit apparaître sur la grille de commande.

<u>Résultats réels</u>:

La mise à jour précédente de la commande a été synchronisée dans la grille (**[!UICONTROL status: Processing]**). Le nouvel ordre n’apparaît jamais sur la grille.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
