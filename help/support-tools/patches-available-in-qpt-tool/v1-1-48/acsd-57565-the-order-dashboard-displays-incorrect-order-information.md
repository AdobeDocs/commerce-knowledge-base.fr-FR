---
title: "ACSD-57565 : le tableau de bord des commandes affiche des informations de commande incorrectes"
description: Appliquez le correctif ACSD-57565 pour résoudre le problème Adobe Commerce en raison duquel le tableau de bord des commandes affiche des informations de commande incorrectes jusqu’à ce que la période soit mise à jour.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 5b292fef-23f6-479f-bf76-adad53d30cf4
source-git-commit: fdf6e6e85f903a26a7b44674937ccf88ee769d06
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57565 : le tableau de bord des commandes affiche des informations de commande incorrectes.

Le correctif ACSD-57565 corrige le problème en raison duquel le tableau de bord des commandes affiche des informations de commande incorrectes jusqu’à ce que la période soit mise à jour. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.48 est installé. L’ID de correctif est ACSD-57565. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le tableau de bord des commandes affiche des informations de commande incorrectes.

<u>Étapes à reproduire</u> :

1. Activez **[!UICONTROL dashboard charts]**.
1. Créez une commande et facturez-la.
1. Patientez pendant au moins 24 heures après la création de la commande.
1. Vérifiez les données **[!UICONTROL dashboard chart]**.
1. Notez le nombre total de commandes.
1. Remplacez l’heure par le *mois en cours*, puis remplacez-le par *aujourd’hui*.

<u>Résultats attendus</u> :

Le tableau de bord doit toujours afficher les statistiques correctes.

<u>Résultats réels</u> :

Le tableau de bord affiche des statistiques incorrectes au premier chargement. Les statistiques précises du graphique sont mises à jour après la période.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
