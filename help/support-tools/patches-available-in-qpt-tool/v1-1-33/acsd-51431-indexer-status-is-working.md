---
title: 'ACSD-51431 : l’état de l’indexeur est *[!UICONTROL Working]* même s’il n’y a aucune entrée dans le changelog'
description: Appliquez le correctif ACSD-51431 pour résoudre le problème Adobe Commerce où l’état de l’indexeur est *[!UICONTROL Working]* même s’il n’y a aucune entrée dans le journal des modifications.
feature: Logs, Price Indexer
role: Admin
exl-id: 85977b78-7f6b-47c7-b33e-16668bdf98fe
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-51431 : l’état de l’indexeur est *[!UICONTROL Working]* même s’il n’y a aucune entrée dans le changelog

Le correctif ACSD-51431 corrige le problème de performances où l’état de l’indexeur est *[!UICONTROL Working]* même s’il n’y a aucune entrée dans le journal des modifications. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.33 est installé. L’ID de correctif est ACSD-51431. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état de l’indexeur est *[!UICONTROL Working]* même s’il n’y a aucune entrée dans le journal des modifications.

<u>Étapes à reproduire</u> :

1. Définissez **[!UICONTROL indexers]** sur [!UICONTROL Update on Schedule].
1. Configurez la tâche cron pour qu’elle s’exécute toutes les minutes.
1. Enregistrez les modifications simultanément dans différents produits.
1. Exécutez `bin/magento indexer:status` en quelques minutes.

<u>Résultats attendus</u> :

Les modifications sont traitées et les indexeurs sont à l’état *[!UICONTROL Ready]*. L’état de *[!UICONTROL Schedule]* est *[!UICONTROL idle (0 in the backlog)]*.

<u>Résultats réels</u> :

Les modifications sont traitées et les indexeurs sont à l’état *[!UICONTROL Ready]*. Cependant, l’état *[!UICONTROL Schedule]* s’affiche *[!UICONTROL working (0 in the backlog)]*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
