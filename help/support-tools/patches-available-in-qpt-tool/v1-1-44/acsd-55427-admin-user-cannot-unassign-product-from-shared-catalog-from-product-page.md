---
title: "ACSD-55427 : un administrateur ne peut pas annuler l’affectation d’un produit à partir de **[!UICONTROL Product in Shared Catalogs]** sur la page du produit"
description: Appliquez le correctif ACSD-55427 pour résoudre le problème Adobe Commerce en raison duquel un produit ne peut pas être annulé à partir de **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
exl-id: 1e08def1-07f6-42e0-b600-9f0bfdd6477a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427 : un administrateur ne peut pas annuler l’affectation d’un produit à **[!UICONTROL Product in Shared Catalogs]** sur la page du produit ;

Le correctif ACSD-55427 corrige le problème en raison duquel vous ne pouvez pas annuler l’affectation d’un produit à partir de **[!UICONTROL Product in Shared Catalogs]** sur la page du produit dans le catalogue de l’administrateur Commerce. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.44 est installée. L’ID de correctif est ACSD-55427. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Vous ne pouvez pas annuler l’affectation d’un produit à **[!UICONTROL Product in Shared Catalogs]** sur la page du produit dans le catalogue de l’administrateur Commerce.

<u>Étapes à reproduire</u>:

Conditions préalables : Adobe Commerce installé avec B2B et **[!UICONTROL Shared Catalogs]** activée.
1. Créez un produit.
1. Accédez au tableau de bord du catalogue partagé et ouvrez le catalogue partagé par défaut.
1. Attribuez le produit au catalogue par défaut et définissez un prix inférieur au prix du produit.
1. Enregistrez le catalogue partagé.
1. Exécutez la variable [!UICONTROL CRON] pour mettre à jour les consommateurs/indexeurs.
1. Ouvrez le produit et supprimez-le de la partie inférieure **[!UICONTROL Product in Shared Catalogs]** .

<u>Résultats attendus</u>:

Le produit doit être supprimé de sous **[!UICONTROL Product in Shared Catalogs]** .

<u>Résultats réels</u>:

Le produit est toujours affiché dans la **[!UICONTROL Product in Shared Catalogs]** .

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
