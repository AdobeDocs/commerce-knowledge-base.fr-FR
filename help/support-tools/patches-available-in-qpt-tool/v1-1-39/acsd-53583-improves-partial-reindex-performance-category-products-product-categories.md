---
title: 'ACSD-53583 : amélioration des performances de réindexation partielle pour les indexeurs [!UICONTROL Category Products] et [!UICONTROL Product Categories]'
description: Appliquez le correctif ACSD-53585 afin d’améliorer les performances de réindexation partielle pour les indexeurs de produits de catégorie et de catégories de produits.
feature: Products, Categories
role: Admin, Developer
exl-id: 1c8f7df3-379f-42d6-8b41-286d34f725d2
source-git-commit: 29c2918ccae6404f6ae87d360ac16b149de5dd0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53583 : amélioration des performances de réindexation partielle pour les indexeurs de produits de catégorie et de catégories de produits

Le correctif ACSD-53583 améliore les performances de réindexation partielle des indexeurs *Category Products* et *Product Categories* . Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.39 est installé. L’ID de correctif est ACSD-53583. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3
* Non compatible avec le module [!DNL Live Search]. Pour appliquer ce correctif à l’installation de [!DNL Live Search], demandez un correctif supplémentaire ACSD-55719.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La réindexation partielle prend plus de temps que la réindexation complète.

<u>Étapes à reproduire</u> :

1. Remplacez tous les indexeurs par *Mise à jour par planification*.
1. Générez des données avec le [!DNL Performance Toolkit] (profil intermédiaire).
1. Apportez des modifications à tous les produits et catégories afin qu’ils soient dans le journal des index et que tous les index soient inactifs.
1. Réindexation partielle pour les indexeurs *Produits de catégorie* et *Catégories de produits*.

<u>Résultats attendus</u> :

La réindexation partielle est appelée une fois par produit et prend presque la même durée que la réindexation complète, car tous les produits et catégories ont été modifiés.

<u>Résultats réels</u> :

La réindexation partielle est appelée plusieurs fois par produit et prend plus de temps que la réindexation complète.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
