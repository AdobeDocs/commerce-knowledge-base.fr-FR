---
title: 'ACSD-58790 : corrige la fonctionnalité de pincement pour zoomer sur les images de la page des détails du produit dans la vue mobile sur [!DNL Chrome]'
description: ACSD-58790 corrige le problème Adobe Commerce en raison duquel l’image dans la vue mobile sur [!DNL Chrome] n’effectuait pas de zoom avant sur l’image comme prévu.
feature: Storefront
role: Admin, Developer
source-git-commit: 51c740dc70937c7b80d8492d02ee4a758f103a35
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-58790 : corrige la fonctionnalité de pincement pour zoomer sur les images de la page des détails du produit dans la vue mobile sur [!DNL Chrome]

Le correctif ACSD-58790 corrige le problème Adobe Commerce en raison duquel l’image dans la vue mobile sur [!DNL Chrome] n’effectuait pas de zoom avant sur l’image comme prévu. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 est installé. L’ID de correctif est ACSD-58790. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Correction de la fonctionnalité de pincement pour zoomer sur les images de page des détails du produit dans la vue mobile sur [!DNL Chrome].

<u>Étapes à reproduire</u> :

1. Créez un produit avec une image.
1. Ouvrez le produit à partir d’un navigateur [!DNL Chrome].
1. Cliquez sur l’image et vérifiez que l’image s’agrandit en double-cliquant dessus.
1. Basculez vers la vue mobile à l’aide des outils de développement [!DNL Chrome].
1. Cliquez sur l’image.
1. Double-appuyez.

<u>Résultats attendus</u> :

L’image est agrandie lorsque vous double-cliquez dessus.

<u>Résultats réels</u> :

L’image n’effectue pas de zoom avant lorsque vous double-cliquez dessus. Ce problème est spécifique à [!DNL Chrome] dans la vue mobile, car la fonctionnalité de zoom fonctionne comme prévu dans [!DNL Firefox].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
