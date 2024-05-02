---
title: 'ACSD-53204: *Le produit ne peut pas être enregistré* erreur lors de demandes simultanées d’ajout d’images à la galerie'
description: Appliquez le correctif ACSD-53204 pour résoudre le problème Adobe Commerce en raison duquel l’erreur *Le produit ne peut pas être enregistré* est générée lors de demandes simultanées d’ajout d’images à la galerie de produits à l’aide du point de terminaison rest/V1/products/&lt;sku&gt;/media .
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: dcea2621-66cf-49d1-bba6-b61c70716e84
source-git-commit: e1ab32a4540ea7483f7f2b8464ef3e4b0ecbbac7
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-53204 : &quot;*Le produit ne peut pas être enregistré*&quot; erreur lors de demandes simultanées d’ajout d’images à la galerie

Le correctif ACSD-53204 corrige le problème où &quot;*Le produit ne peut pas être enregistré*&quot;une erreur est générée lors de demandes simultanées d’ajout d’images à la galerie de produits à l’aide de la variable `rest/V1/products/<sku>/media` point de terminaison . Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.39 est installée. L’ID de correctif est ACSD-53204. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

&quot;*Le produit ne peut pas être enregistré*&quot;une erreur est générée lors de demandes simultanées d’ajout d’images à la galerie de produits à l’aide de la variable `rest/V1/products/<sku>/media` point de terminaison .

<u>Étapes à reproduire</u>:

1. Connectez-vous au panneau d’administration.
1. Créez un produit avec SKU p1.
1. Exécutez plusieurs requêtes simultanées sur la variable `rest/V1/products/<sku>/media` point de fin pour télécharger plusieurs images simultanément.

<u>Résultats attendus</u>:

Les images sont enregistrées sans erreur.

<u>Résultats réels</u>:

&quot;*Le produit ne peut pas être enregistré*&quot; est renvoyée de temps à autre.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
