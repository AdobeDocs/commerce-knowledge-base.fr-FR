---
title: 'ACSD-55566: [!UICONTROL mergeCart] Échec de la mutation avec une erreur de serveur interne dans [!DNL GraphQL] response'
description: Appliquez le correctif ACSD-5566 pour résoudre le problème Adobe Commerce en raison duquel la mutation `mergeCart` échoue avec une erreur de serveur interne dans [!DNL GraphQL] lors de la fusion de la source et des paniers de destination ayant les mêmes éléments de lot.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84a9b861-351e-4fcc-bb91-3e31c7ae24e6
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-55566 : `mergeCart` Échec de la mutation avec une erreur de serveur interne dans [!DNL GraphQL] response

Le correctif ACSD-5566 corrige le problème où la variable `mergeCart` Échec de la mutation avec une erreur de serveur interne dans [!DNL GraphQL] réponse. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.48 est installée. L’ID de correctif est ACSD-55566. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`mergeCart` Échec de la mutation avec une erreur de serveur interne dans [!DNL GraphQL] lors de la fusion de la source et des paniers de destination ayant les mêmes éléments de lot.

<u>Étapes à reproduire</u>:

1. Créez une source personnalisée et un stock personnalisé.
1. Affectez le stock créé au site web principal.
1. Créez un produit simple et affectez-lui la source créée (qty=2).
1. Créez un lot de produits avec une option et un produit enfant (produit créé à l’étape 3).
1. Création d’un panier d’invité via [!DNL GraphQL].
1. Ajoutez un produit groupé avec les deux options sélectionnées.
1. Enregistrez le *cartID*.
1. Créez un client et générez un jeton client.
1. Créez un panier client.
1. Ajoutez le même produit groupé avec la même configuration au panier.
1. Essayez de fusionner le panier d’invité avec le panier du client.

<u>Résultats attendus</u>:

Le panier client contient des produits des deux paniers.

<u>Résultats réels</u>:

Vous obtenez une erreur interne.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
