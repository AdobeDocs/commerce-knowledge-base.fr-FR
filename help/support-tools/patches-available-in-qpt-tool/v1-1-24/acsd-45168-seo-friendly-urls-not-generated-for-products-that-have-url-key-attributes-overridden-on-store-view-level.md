---
title: "ACSD-45168 : URL compatibles avec le SEO non générées pour les produits dont les attributs url_key sont remplacés"
description: Appliquez le correctif ACSD-45168 pour résoudre le problème Adobe Commerce en raison duquel les URL compatibles avec l’optimisation pour les moteurs de recherche n’étaient pas générées pour les produits dont les attributs url_key sont remplacés au niveau de l’affichage en magasin.
exl-id: cdba42ac-3c96-439b-befa-f0a13587b5d9
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-45168 : URL compatibles SEO non générées pour les produits dont les attributs url_key sont remplacés

Le correctif ACSD-45168 corrige le problème en raison duquel les URL compatibles avec l’optimisation pour les moteurs de recherche ne sont pas générées pour les produits dont les attributs url_key sont remplacés au niveau de l’affichage de magasin. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.24 est installée. L’ID de correctif est ACSD-45168. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les URL compatibles avec l’optimisation pour les moteurs de recherche ne sont pas générées pour les produits dont les attributs url_key sont remplacés au niveau de l’affichage de magasin.

<u>Étapes à reproduire</u>:

1. Définissez la configuration comme suit en accédant à la fonction **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**:
   * [!UICONTROL Use Categories Path for Product URLs] = *Oui*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Oui*
1. Nettoyez le cache de configuration.
1. Créez deux catégories : [!UICONTROL Category 1] et [!UICONTROL Category 2].
1. Créez deux produits : [!UICONTROL Product 1] in [!UICONTROL Category 1], [!UICONTROL Product 2] in [!UICONTROL Category 1].
1. Remplacez la portée par [!UICONTROL Default Store View] pour [!UICONTROL Product 1].
1. Décochez l’URL facultative [!UICONTROL Key] in [!UICONTROL Search Engine Optimization].
1. Enregistrez le produit.
1. Revenir à [!UICONTROL All Store Views].
1. Ajouter [!UICONTROL Product 1] to [!UICONTROL Category 2]et ajoutez [!UICONTROL Product 2] to [!UICONTROL Category 2].
1. Vérifiez les [!UICONTROL url_rewrite] table ou [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Résultats attendus</u>:

URL conviviale pour l’optimisation pour les moteurs de recherche [!UICONTROL Category 2] est créé pour [!UICONTROL Product 1].

<u>Résultats réels</u>:

URL conviviale pour l’optimisation pour les moteurs de recherche [!UICONTROL Category 2] est manquant pour [!UICONTROL Product 1] car l’attribut de clé d’URL a été remplacé pour la portée de la vue de magasin.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
