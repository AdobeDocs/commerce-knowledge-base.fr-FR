---
title: "ACSD-48587 : le widget de produit ne fonctionne pas avec les SKU contenant des caractères d’HTML"
description: Appliquez le correctif ACSD-48587 pour résoudre le problème Adobe Commerce en raison duquel les caractères spéciaux HTMLS dans les règles de correspondance du widget de produits les empêchent d’afficher les produits correspondants.
exl-id: 9f8f436c-f3ef-4510-a941-12f701e7524e
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48587 : le widget de produit ne fonctionne pas avec les SKU contenant des caractères d’HTML.

Le correctif ACSD-48587 corrige le problème en raison duquel les caractères spéciaux HTMLS dans les règles de correspondance du widget de produits les empêchaient d’afficher les produits correspondants. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 est installé. L’ID de correctif est ACSD-48587. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le widget de produit ne fonctionne pas avec les SKU contenant les symboles *&quot;&amp;&quot;*.

<u>Étapes à reproduire</u> :

1. Créez un produit contenant *&quot;&amp;&quot;* dans le SKU (par exemple, s000&amp;01).
1. Modifiez le contenu d’une page CMS sur le *Page Builder*.
1. Ajoutez un widget de produits.
1. Modifiez le widget et définissez **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. Saisissez le SKU qui contient *&quot;&amp;&quot;* dans le champ des SKU du produit.
1. Enregistrez le contenu et la page CMS.
1. Vérifiez le contenu de la *page CMS* pour l’ *aperçu du générateur de page* et le storefront de produit.

<u>Résultats attendus</u> :

Le produit avec *&quot;&amp;&quot;* dans le SKU s’affiche dans l’aperçu du créateur de pages et sur le storefront.

<u>Résultats réels</u> :

Le produit avec *&quot;&amp;&quot;* dans le SKU ne s’affiche pas dans l’aperçu du créateur de pages.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
