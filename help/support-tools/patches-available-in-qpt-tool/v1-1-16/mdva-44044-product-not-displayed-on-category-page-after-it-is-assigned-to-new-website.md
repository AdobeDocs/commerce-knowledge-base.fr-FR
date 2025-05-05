---
title: "MDVA-44044 : produit non affiché sur la page de catégorie après avoir été affecté au nouveau site web"
description: Le correctif MDVA-44044 résout le problème lorsqu’un produit ne s’affiche pas sur la page de catégorie après avoir été affecté à un nouveau site web. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 est installé. L’ID de correctif est MDVA-44044. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: e3a179ed-243c-4200-a01a-796657bd31ab
feature: Categories, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-44044 : produit non affiché sur la page de catégorie après son affectation à un nouveau site web

Le correctif MDVA-44044 résout le problème lorsqu’un produit ne s’affiche pas sur la page de catégorie après avoir été affecté à un nouveau site web. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 est installé. L’ID de correctif est MDVA-44044. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit ne s’affiche pas sur la page de catégorie une fois qu’il a été affecté à un nouveau site web.

<u>Étapes à reproduire</u> :

1. Définissez le mode indexeur pour planifier.
1. Créez un site web secondaire, un magasin et une vue de magasin.
1. Ajoutez un code de magasin secondaire dans `index.php` :

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. Créez une nouvelle catégorie.
1. Créez un produit affecté à la catégorie nouvellement créée. Veillez à ne l’affecter qu’au site web principal.
1. Lancez le cron.
1. Ouvrez la catégorie à partir du storefront.
1. Affectez le produit au site web secondaire.
1. Exécutez à nouveau le cron.

<u>Résultats attendus</u> :

Le produit apparaît sur la page de catégorie après un indexeur planifié.

<u>Résultats réels</u> :

Le produit n’apparaît pas sur la page de catégorie tant qu’une réindexation complète n’a pas été effectuée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
