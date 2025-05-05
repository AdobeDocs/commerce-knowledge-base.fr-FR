---
title: 'ACSD-57337 : un utilisateur administrateur avec des restrictions d’accès peut afficher toutes les entreprises dans la grille *Entreprises*'
description: Appliquez le correctif ACSD-57337 pour résoudre le problème Adobe Commerce en raison duquel un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques pouvait afficher les sociétés de tous les sites de la grille *Entreprises*.
feature: Companies, B2B, Configuration
role: Admin, Developer
exl-id: e49289a1-fe86-42b7-8d93-71f35b5e318d
source-git-commit: 33a9cb0227b318a0fff135621ecd6642f2fa827a
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-57337 : Un utilisateur administrateur avec des restrictions d’accès peut afficher toutes les entreprises dans la grille *Entreprises*

Le correctif ACSD-57337 corrige le problème lorsqu’un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques pouvait afficher les entreprises de tous les sites web de la grille *Entreprises*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 est installé. L’ID de correctif est ACSD-57337. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques peut afficher les entreprises de tous les sites web de la grille *Entreprises*.

<u>Étapes à reproduire</u> :

1. Créez un site web, un magasin et un storeview supplémentaires.
1. Créez quelques entreprises affectées à différents sites web.
1. Créez un rôle d’utilisateur administrateur et définissez la portée du rôle sur le site web créé.
1. Créez un administrateur et affectez-le au rôle créé.
1. Connectez-vous avec un nouvel administrateur.
1. Ouvrez **[!UICONTROL Customers]** > **[!UICONTROL Companies]** et observez la liste des entreprises.

<u>Résultats attendus</u> :

Les entreprises qui ont été affectées au site web supplémentaire sont visibles dans la grille *Entreprises* .

<u>Résultats réels</u> :

Toutes les entreprises sont visibles dans la grille *Entreprises*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
