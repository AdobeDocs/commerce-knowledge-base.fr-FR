---
title: 'ACSD-53658: **[!UICONTROL Recently Viewed Product]** données non mises à jour correctement dans la vue de magasin'
description: Appliquez le correctif ACSD-53658 pour résoudre le problème Adobe Commerce en raison duquel les données **[!UICONTROL Recently Viewed Product]** ne sont pas mises à jour correctement dans la vue de magasin.
feature: CMS, Personalization
role: Admin, Developer
exl-id: 4086dcee-37e5-4393-9048-ce19a2d248e9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-53658 : **[!UICONTROL Recently Viewed Product]** données non mises à jour correctement dans la vue de magasin

Le correctif ACSD-53658 corrige le problème en raison duquel les données **[!UICONTROL Recently Viewed Product]** ne sont pas mises à jour correctement dans la vue de magasin. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 est installé. L’ID de correctif est ACSD-53658. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les données **[!UICONTROL Recently Viewed Product]** ne sont pas mises à jour correctement dans la vue de magasin.

<u>Étapes à reproduire</u> :

1. Connectez-vous au panneau Admin.
1. Créez une deuxième vue de magasin pour le site web par défaut.
1. Créez un produit simple.
1. Définissez un nom de produit différent pour la nouvelle vue de magasin.
1. Créez un widget **[!UICONTROL Recently Viewed Product]**.
1. Configurez ce widget pour qu’il s’affiche sur la page d’accueil.
1. Ouvrez la page de produit sur Storefront à partir de la vue de magasin par défaut.
1. Ouvrez la page Accueil .
1. À l’aide du sélecteur de magasin, basculez vers la deuxième vue de magasin.

<u>Résultats attendus</u> :

Le nom du produit est mis à jour dans le widget.

<u>Résultats réels</u> :

Le nom du produit n’est pas mis à jour dans le widget.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
