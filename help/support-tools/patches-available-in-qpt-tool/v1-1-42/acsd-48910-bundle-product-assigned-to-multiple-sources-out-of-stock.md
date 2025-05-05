---
title: "ACSD-48910 : Le produit groupé attribué plusieurs sources est en rupture de stock après facture et livraison"
description: Appliquez le correctif ACSD-48910 pour résoudre le problème Adobe Commerce en raison duquel le produit groupé affecté à plusieurs sources est en rupture de stock après la facturation et l’expédition d’une commande, même s’il a toujours une quantité non nulle.
feature: Products, Inventory
role: Admin, Developer
exl-id: 6ac3dedf-1c28-4874-b963-44a429b37983
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-48910 : Le produit groupé attribué plusieurs sources est en rupture de stock après facture et livraison

Le correctif ACSD-48910 corrige le problème en raison duquel le produit assemblé affecté à plusieurs sources est en rupture de stock après la facturation et l’expédition d’une commande, même s’il a toujours une quantité non nulle. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 est installé. L’ID de correctif est ACSD-48910. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit fourni affecté à plusieurs sources est en rupture de stock après facturation et livraison, même s’il est toujours disponible.

<u>Étapes à reproduire</u> :

1. Créez deux sites web.
1. Créez deux magasins/vues de magasin (une par site web).
1. Créez deux produits simples (quantité = 10) et attribuez-les aux stocks et aux sites web.
1. Créez un produit regroupé et ajoutez-lui ces produits simples. Affectez le produit fourni aux deux sites web.
1. Positionnez-vous sur le storefront et ajoutez le produit fourni au panier.
1. Consultez et passez la commande.
1. À partir de l’administrateur, facturez et expédiez la commande.

<u>Résultats attendus</u> :

Le produit groupé reste en stock puisque nous n’avons acheté que 1 des 10 articles.

<u>Résultats réels</u> :

Le produit regroupé passe de son état en état hors stock.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
