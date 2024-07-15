---
title: "ACSD-51984 : Les valeurs des champs de produit non cochées [!UICONTROL Use Default Value] et non par défaut ne sont pas enregistrées pour le deuxième site web, magasin et vue de magasin"
description: Appliquez le correctif ACSD-51984 pour résoudre le problème Adobe Commerce en raison duquel les valeurs des champs de produit non cochées [!UICONTROL Use Default Value] et non par défaut ne sont pas enregistrées pour le deuxième site web, magasin et magasin.
feature: Products
role: Admin
exl-id: 1f45c700-dd27-4a69-8634-9c0aa131d197
source-git-commit: f42fcacbe3b7174b2a3571afe80f5eedb8e9aa75
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# ACSD-51984 : Les valeurs des champs de produit non cochées *[!UICONTROL Use Default Value]* et non par défaut ne sont pas enregistrées.

>[!NOTE]
>
>Ce correctif est obsolète et a été remplacé par le correctif [ACSD-54776](/help/support-tools/patches-available-in-qpt-tool/v1-1-39/acsd-54776-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) ajouté dans la version 1.1.39 QPT.

Le correctif ACSD-51984 corrige le problème en raison duquel les valeurs des champs de produit non cochées **[!UICONTROL Use Default Value]** et non par défaut ne sont pas enregistrées pour le deuxième site web, magasin et magasin. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 est installé. L’ID de correctif est ACSD-51984. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les valeurs de champ de produit non cochées *[!UICONTROL Use Default Value]* et autres que par défaut ne sont pas enregistrées pour la deuxième vue de site web, de magasin et de magasin.

<u>Étapes à reproduire</u> :

1. Accédez au serveur principal et accédez à **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** et créez un site web, un magasin et une vue de magasin.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, créez un produit simple et enregistrez-le, puis affectez-le aux deux sites Web, à partir du **[!UICONTROL Product in Websites]**.
1. Remplacez la portée par la nouvelle vue de magasin de l’étape 2.
1. Accédez à **[!UICONTROL Search Engine Optimization]** et désélectionnez les cases **[!UICONTROL Use Default Value]** pour [!UICONTROL Meta Title], [!UICONTROL Meta Keywords] et [!UICONTROL Meta Description].
1. Nettoyez le texte des champs : *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* et *[!UICONTROL Meta Description]*, puis cliquez sur **[!UICONTROL Save]**.
1. Accédez à nouveau à **[!UICONTROL Search Engine Optimization]**.

<u>Résultats attendus</u>

Les valeurs des champs et des cases à cocher sont enregistrées.

<u>Résultats réels</u>

Les valeurs des champs et des cases à cocher ne sont pas enregistrées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide [!DNL Quality Patches Tool].