---
title: "ACSD-53118 : les règles du panier avec coupon ne fonctionnent pas correctement"
description: Appliquez le correctif ACSD-53118 pour résoudre le problème Adobe Commerce en raison duquel la règle de prix du panier est appliquée à l’aide d’un code de bon alors que le produit dans le panier a un attribut correspondant vide.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: a660ddb3-03fc-4460-b2a8-8e851f57e7a9
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-53118 : les règles du panier avec coupon ne fonctionnent pas correctement

Le correctif ACSD-53118 corrige le problème en raison duquel la règle de prix du panier est appliquée à l’aide d’un code de bon alors que le produit dans le panier a un attribut de correspondance vide. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.41 est installée. L’ID de correctif est ACSD-53118. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La règle de prix du panier est appliquée à l’aide d’un code de bon alors que le produit du panier possède un attribut correspondant vide.

<u>Étapes à reproduire</u>:

1. Créez un attribut de prix et ajoutez-le au jeu d’attributs. Rendre l’attribut utilisable dans les conditions de règle de promotion.
1. Créez un produit et laissez le nouvel attribut vide.
1. Créez une règle de prix de panier avec un bon spécifique et la condition suivante :

   * Si un élément est TROUVÉ dans le panier avec TOUTES ces conditions true : Attribute1 est 0.

1. Ajoutez le produit créé à l’étape 2 au panier.
1. Utilisez le code de coupon pour la règle de panier créée à l’étape 3.

<u>Résultats attendus</u>:

La remise n’est pas appliquée au panier.

<u>Résultats réels</u>:

La remise est appliquée au panier.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
