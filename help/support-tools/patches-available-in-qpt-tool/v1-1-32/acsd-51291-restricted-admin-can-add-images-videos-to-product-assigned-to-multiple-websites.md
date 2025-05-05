---
title: "ACSD-51291 : l’administrateur restreint peut ajouter des images/vidéos au produit affecté à plusieurs sites web"
description: Appliquez le correctif ACSD-51291 pour résoudre le problème Adobe Commerce en raison duquel un administrateur restreint ayant accès à un site web peut ajouter des images/vidéos à un produit affecté à plusieurs sites web.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: d3cf5009-6b80-4841-95c3-75bb15c9c0a4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# ACSD-51291 : l’administrateur restreint peut ajouter des images/vidéos à un produit affecté à plusieurs sites web.

Le correctif ACSD-51291 corrige le problème lorsqu’un administrateur restreint ayant accès à un site web peut ajouter des images/vidéos à un produit affecté à plusieurs sites web. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 est installé. L’ID de correctif est ACSD-51291. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un administrateur restreint ayant accès à un site web peut ajouter des images/vidéos à un produit affecté à plusieurs sites web.

<u>Étapes à reproduire</u>

1. Connectez-vous en tant qu’administrateur.
1. Créez un second site web, une deuxième vue de magasin et de magasin.
1. Créez un second rôle d’administrateur avec des ressources uniquement pour la deuxième vue de site web, de magasin et de magasin.
1. Créez un second administrateur et affectez-le au nouveau rôle d’administrateur restreint.
1. Créez un produit et affectez-le aux sites web par défaut et aux nouveaux sites web.
1. Déconnectez-vous du profil administrateur principal.
1. Connectez-vous en tant que nouvel administrateur restreint.
1. Modifiez le produit créé, qui a été affecté aux deux sites web.
1. Ouvrez l’onglet **[!UICONTROL Images and Videos]** .

<u>Résultats attendus</u> :

* Le message suivant s&#39;affiche :

  *L’administrateur restreint est autorisé à effectuer des actions avec des images ou des vidéos, uniquement lorsque l’administrateur a des droits sur tous les sites web auxquels le produit est affecté.*

* Le bouton **[!UICONTROL Add Video]** n&#39;est pas actif.

<u>Résultats réels</u> :

L’administrateur restreint peut ajouter des images et des vidéos même lorsque le produit est affecté à un site web auquel il n’a pas accès.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
