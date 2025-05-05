---
title: "ACSD-51884 : chemin du cache de l’image du produit incorrect sur la commande de redimensionnement"
description: Appliquez le correctif ACSD-51884 pour résoudre le problème Adobe Commerce en raison duquel le chemin du cache de l’image du produit devient incorrect après l’exécution de la commande de redimensionnement.
feature: Products
role: Admin
exl-id: cf542c4b-07b1-4f05-95bc-82bc098bcd4d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-51884 : chemin du cache de l’image du produit incorrect sur la commande de redimensionnement

Le correctif ACSD-51884 corrige le problème en raison duquel une erreur interne où le chemin du cache de l’image du produit est incorrect après l’exécution de la commande resize. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.37 est installé. L’ID de correctif est ACSD-51884. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le chemin du cache de l’image du produit est incorrect lors de la commande resize.

<u>Étapes à reproduire</u> :

1. Créez un site web/magasin/storeview.
1. Créez un produit, puis affectez-le à des sites web et chargez l’image du produit.
1. Créez un thème (voir le fichier joint Adobe.zip).
1. Dans `app/design/Adobe/theme/etc/view.xml` change :

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

to

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. Appliquez le thème à la vue de magasin créée précédemment.
1. Consultez la page produit du 2e site web. L’image du produit s’affiche correctement.
1. Utiliser le cache de purge :
   `bin/magento cache:flush`
1. Consultez la page produit du 2e site web.

<u>Résultats attendus</u> :

L’image du produit s’affiche correctement.

<u>Résultats réels</u> :

L’image du produit n’existe pas.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
