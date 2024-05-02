---
title: "ACSD-47137 : amélioration de la vitesse de chargement de la galerie d’images `pub/media` folder big"
description: Appliquez le correctif ACSD-47137 pour améliorer la vitesse de chargement de la galerie d’images lorsque le dossier "pub/media" est très volumineux.
exl-id: 43268909-6845-4d1d-b6b8-4ae0ce40fd5e
feature: Cache, Catalog Management, Categories, Media
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-47137 : amélioration de la vitesse de chargement de la galerie d’images lors de la `pub/media` Dossier volumineux

Le correctif ACSD-47137 améliore la vitesse de chargement de la galerie d’images lors de la `pub/media` Le dossier est très grand. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.24 est installée. L’ID de correctif est ACSD-47137. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La vitesse de chargement de la galerie d’images est lente lorsque la variable `pub/media` Le dossier est très grand.

<u>Étapes à reproduire</u>:

1. Accédez à Administration Adobe Commerce > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** to _Non_.
1. Nettoyez le cache de configuration.
1. Déconnectez-vous et reconnectez-vous en tant qu’utilisateur administrateur.
1. Dans la barre latérale d’administration, accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** et sélectionnez la catégorie racine.
1. Développez l’objet **[!UICONTROL Content]** et cliquez sur **[!UICONTROL Select from Gallery]**.

Lors du chargement de la page, Adobe Commerce envoie `media_gallery/directories/gettree` demande de chargement de l’arborescence de dossiers multimédia.

<u>Résultats attendus</u>:

La variable `media_gallery/directories/gettree` La requête ne doit charger le contenu que depuis les répertoires nécessaires, à l’exception de la boucle de la liste complète de chemins d’accès depuis la `pub/media/` dossier.

<u>Résultats réels</u>:

La variable `media_gallery/directories/gettree` le chargement de la requête prend beaucoup de temps lorsque la variable `pub/media/` a beaucoup de contenu.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
