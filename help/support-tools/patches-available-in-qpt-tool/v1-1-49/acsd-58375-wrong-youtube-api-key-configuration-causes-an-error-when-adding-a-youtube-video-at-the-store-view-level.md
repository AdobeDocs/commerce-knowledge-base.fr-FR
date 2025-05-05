---
title: "ACSD-58375 : Une clé d’API YouTube mal configurée entraîne une erreur lors de l’ajout de la vidéo au niveau de l’affichage du magasin"
description: Appliquez le correctif ACSD-58375 pour résoudre le problème Adobe Commerce en raison duquel une configuration de clé API YouTube incorrecte provoque une erreur lors de l’ajout d’une vidéo YouTube au niveau de l’affichage du magasin.
feature: Catalog Management, Configuration
role: Admin, Developer
source-git-commit: 1887a74b0c5545f9213f54602c58de7028d1ad72
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-58735 : Une clé d’API YouTube mal configurée entraîne une erreur lors de l’ajout de vidéos au niveau de l’affichage de magasin.

Le correctif ACSD-58735 corrige le problème en raison duquel une configuration de clé de l’API YouTube incorrecte provoquait une erreur lors de l’ajout d’une vidéo YouTube au niveau de l’affichage du magasin. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 est installé. L’ID de correctif est ACSD-58735. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une mauvaise configuration de la clé d’API YouTube entraîne une erreur lors de l’ajout d’une vidéo YouTube au niveau de l’affichage du magasin.

<u>Étapes à reproduire</u> :

1. Accédez à Admin > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]**.
1. Remplacez le niveau *Scope* par *[!UICONTROL Main Website]*.
1. Ajoutez la clé de l’API YouTube.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Sélectionnez n’importe quel produit et faites défiler l’écran jusqu’à *[!UICONTROL Images and Video]*. Cliquez sur **[!UICONTROL Add Video]**.
1. Copiez un lien vidéo YouTube et collez-le dans le champ de lien vidéo. Sortez du champ.

<u>Résultats attendus</u> :

La clé API YouTube a une portée globale et est masquée au niveau du site web.

<u>Résultats réels</u> :

L’erreur suivante est générée : *La vidéo n’est pas affichée pour la raison suivante : clé API non valide. Veuillez transmettre une clé API valide*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
