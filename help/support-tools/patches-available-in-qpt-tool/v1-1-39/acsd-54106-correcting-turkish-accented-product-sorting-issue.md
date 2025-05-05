---
title: "ACSD-54106 : correction du tri des caractères accentués turcs dans la catégorie de produits"
description: Appliquez le correctif ACSD-54106 pour résoudre le problème Adobe Commerce en raison duquel le tri par nom des produits de catégorie pour les caractères accentués turcs est incorrect.
feature: Categories, Products, Search
role: Admin
exl-id: 80386ded-4ada-4822-b073-f477ca123093
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-54106 : correction du tri des caractères accentués turcs dans la catégorie de produits

Le correctif ACSD-54106 corrige le problème en raison duquel le tri par nom des produits de catégorie pour les caractères accentués turcs est incorrect. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 est installé. L’ID de correctif est ACSD-54106. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le tri des produits par nom dans les catégories est incorrect pour les caractères accentués turcs.

<u>Étapes à reproduire</u> :

1. Connectez-vous au panneau d’administration.
1. Créez des produits simples nommés comme suit et affectez-les à n’importe quelle catégorie :

* Nom A
* Nom :
* Nom D
* Nom Ğ
* Nom M
* Nom Ö
* Nom : précisément
* Nom Y
* Nom Z

1. Accédez au storefront et à la catégorie contenant les produits.
1. Modifiez l’ordre de tri sur *[!UICONTROL By Name]*.

<u>Résultats attendus</u> :

Les produits sont correctement triés dans l’ordre suivant :

* Nom A
* Nom :
* Nom D
* Nom Ğ
* Nom M
* Nom Ö
* Nom : précisément
* Nom Y
* Nom Z

<u>Résultats réels</u> :

Les produits sont incorrectement triés dans l’ordre suivant :

* Nom A
* Nom D
* Nom M
* Nom Y
* Nom Z
* Nom :
* Nom Ö
* Nom : précisément
* Nom Ğ

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
