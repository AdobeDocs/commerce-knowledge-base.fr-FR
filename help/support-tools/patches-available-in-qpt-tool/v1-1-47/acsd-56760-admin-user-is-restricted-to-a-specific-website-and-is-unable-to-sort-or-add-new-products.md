---
title: "ACSD-56760 : l’utilisateur administrateur est limité à un site web spécifique et ne peut pas trier ni ajouter de nouveaux produits"
description: Appliquez le correctif ACSD-56760 pour résoudre le problème Adobe Commerce en raison duquel l’utilisateur administrateur qui se limite à un site web spécifique et ne peut pas trier ou ajouter de nouveaux produits dans une catégorie si le magasin web possède sa propre catégorie racine.
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760 : l’utilisateur administrateur est limité à un site web spécifique et ne peut pas trier ni ajouter de nouveaux produits.

Le correctif ACSD-56760 corrige le problème en raison duquel l’utilisateur administrateur qui se limite à un site web spécifique et ne peut pas trier ou ajouter de nouveaux produits dans une catégorie au cas où le magasin web possède sa propre catégorie racine. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.47 est installé. L’ID de correctif est ACSD-56760. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Utilisateur administrateur qui se limite à un site web spécifique et qui ne peut pas trier ou ajouter de nouveaux produits dans une catégorie au cas où le magasin web possède sa propre catégorie racine.

<u>Étapes à reproduire</u> :

1. Créez des sites web *2*.
1. Créez un **[!UICONTROL restricted admin user]** ayant accès uniquement au site web *1*.
1. Connectez-vous en tant que **[!UICONTROL restricted admin user]** et essayez de modifier les positions de produit dans une catégorie.

*Cas 1* :

* *2* magasins.
* Catégories racine *2*, chaque site web est affecté à sa propre racine de catégorie.

*Cas 2* :

* *2* magasins.
* Seule la catégorie racine *1* est affectée aux deux sites Web.

<u>Résultats attendus</u> :

* *Cas 1* : l’administrateur restreint doit pouvoir trier les produits dans la catégorie disponible.
* *Cas 2* : l’administrateur restreint ne peut pas trier les produits dans la catégorie disponible, car cela aura également une incidence sur la boutique restreinte.

<u>Résultats réels</u> :

* *Cas 1* : l’administrateur restreint ne peut pas trier les produits dans la catégorie disponible.
* *Cas 2* : l’administrateur restreint peut trier les produits à l’intérieur de la catégorie disponible, ce qui affecte les boutiques restreintes.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
