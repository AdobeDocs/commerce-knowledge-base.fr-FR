---
title: 'ACSD-49129 : attribut "Contenu" non renvoyé dans les réponses de l’API de média de produit'
description: Appliquez le correctif ACSD-49129 pour résoudre le problème Adobe Commerce en raison duquel l’attribut *content* (*code image base64*) n’est pas renvoyé dans les réponses de l’API média du produit "rest/V1/products/sku/media".
exl-id: b7022046-3f52-4880-81b8-977ed270773f
feature: REST, Attributes, Media, Page Content, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-49129 : attribut &quot;Contenu&quot; non renvoyé dans les réponses de l’API de média de produit

Le correctif ACSD-49129 corrige le problème en raison duquel l’attribut *content* (*[!UICONTROL base64 image code]*) n’est pas renvoyé dans les réponses de l’API de média de produit `rest/V1/products/sku/media`. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.30 est installé. L’ID de correctif est ACSD-49129. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut *content* (*[!UICONTROL base64 image code]*) n’est pas renvoyé dans les réponses de l’API de média de produit `rest/V1/products/sku/media`.

<u>Étapes à reproduire</u> :

1. Créez un produit avec une image.
1. Envoyez la requête *API REST GET* à `rest/V1/products/<sku>/media` et `rest/V1/products/<sku>/media/<entryId>`.
1. Vérifiez les réponses de l’API.

<u>Résultats attendus</u>

L&#39;attribut *content* avec les données est disponible via l&#39;API REST.

<u>Résultats réels</u>

L&#39;attribut *content* n&#39;est pas présent dans les réponses de l&#39;API.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
