---
title: '''ACSD-49628: [!DNL Page Builder] Erreurs CORS empêchant l’enregistrement du produit"'
description: Appliquez le correctif ACSD-49628 pour résoudre le problème Adobe Commerce où la variable [!DNL Page Builder] Les erreurs CORS empêchent l’enregistrement du produit.
exl-id: c6e2f0b3-aea0-4caf-8b69-9644b38c909c
feature: Categories, Page Builder, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49628 : [!DNL Page Builder] Les erreurs CORS empêchent l’enregistrement des produits

Le correctif ACSD-49628 corrige le problème où [!DNL Page Builder] Les erreurs CORS empêchent un administrateur d’enregistrer un produit. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.32 est installée. L’ID de correctif est ACSD-49628. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL Page Builder] Les erreurs CORS empêchent l’enregistrement d’un produit.

<u>Étapes à reproduire</u>:

1. Connectez-vous en tant qu’administrateur.
1. Créez un rôle utilisateur avec les autorisations suivantes :

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. N’ajoutez pas de *[!UICONTROL Content]* autorisations.
1. Créez un autre utilisateur administrateur et affectez les rôles créés ci-dessus à cet utilisateur.
1. Créez un produit et déconnectez-vous.
1. Connectez-vous en tant que second administrateur.
1. Essayez de modifier et d’enregistrer le produit.

<u>Résultats attendus</u>:

Le deuxième administrateur peut enregistrer le produit, mais la variable **[!UICONTROL Edit with Page Builder]** n’est pas affiché pour l’administrateur sans aucun *[!UICONTROL Content]* autorisations.

<u>Résultats réels</u>:

Le deuxième administrateur ne peut pas enregistrer le produit en raison de plusieurs [!DNL Page Builder] erreurs.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
