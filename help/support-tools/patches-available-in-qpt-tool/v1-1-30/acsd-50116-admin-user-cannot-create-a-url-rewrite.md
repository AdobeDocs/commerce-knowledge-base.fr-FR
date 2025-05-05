---
title: "ACSD-50116 : un utilisateur administrateur ne peut pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur"
description: Appliquez le correctif ACSD-50116 pour résoudre le problème Adobe Commerce en raison duquel un utilisateur administrateur ne peut pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur.
exl-id: 3fa8ebc1-b55d-437e-9dc7-bf6c300b9bbe
feature: Admin Workspace, Categories
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-50116 : un utilisateur administrateur ne peut pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur.

Le correctif ACSD-50116 corrige le problème lorsqu’un utilisateur administrateur ne peut pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 est installé. L’ID de correctif est ACSD-50116. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un utilisateur administrateur ne peut pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur.

<u>Étapes à reproduire</u> :

1. Créez une arborescence de catégories comportant plus de trois niveaux de sous-catégories.
1. Essayez de créer un *[!UICONTROL URL Rewrite]* pour la catégorie de niveau 4 à l’aide des options *[!UICONTROL For Product]* et *[!UICONTROL For Category]* .

<u>Résultats attendus</u> :

L’arborescence des catégories affiche les sous-catégories jusqu’au niveau quatre ou inférieur.

<u>Résultats réels</u> :

L’arborescence des catégories n’affiche que trois sous-catégories au maximum.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
