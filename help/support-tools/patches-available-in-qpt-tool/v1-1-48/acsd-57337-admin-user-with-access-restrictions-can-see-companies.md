---
title: "ACSD-57337 : Un utilisateur administrateur avec des restrictions d’accès peut afficher toutes les entreprises dans la grille *Entreprises*"
description: Appliquez le correctif ACSD-57337 pour résoudre le problème Adobe Commerce en raison duquel un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques pouvait afficher les sociétés de tous les sites de la grille *Entreprises*.
feature: Companies, B2B, Configuration
role: Admin, Developer
source-git-commit: a02c80006f1c8a434fe17322f0c6cee25f086396
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-57337 : Un utilisateur administrateur avec des restrictions d’accès peut afficher toutes les entreprises dans la variable *Entreprises* grid

Le correctif ACSD-57337 corrige le problème en raison duquel un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques pouvait afficher les entreprises de tous les sites du *Entreprises* grid. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.48 est installée. L’ID de correctif est ACSD-57337. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques peut afficher les entreprises de tous les sites du *Entreprises* grid.

<u>Étapes à reproduire</u>:

1. Créez un site web, un magasin et un storeview supplémentaires.
1. Créez quelques entreprises affectées à différents sites web.
1. Créez un rôle d’utilisateur administrateur et définissez la portée du rôle sur le site web créé.
1. Créez un administrateur et affectez-le au rôle créé.
1. Connectez-vous avec un nouvel administrateur.
1. Ouvrir **[!UICONTROL Customers]** > **[!UICONTROL Companies]** et consulter la liste des entreprises.

<u>Résultats attendus</u>:

Les entreprises qui ont été affectées au site web supplémentaire sont visibles dans la variable *Entreprises* grid.

<u>Résultats réels</u>:

Toutes les entreprises sont visibles dans la variable *Entreprises* grid.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.