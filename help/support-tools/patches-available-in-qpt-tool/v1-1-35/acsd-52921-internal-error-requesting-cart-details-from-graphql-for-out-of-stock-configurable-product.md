---
title: "ACSD-52921 : erreur de demande de détails de panier auprès de GraphQL pour un produit configurable en rupture de stock"
description: Appliquez le correctif ACSD-52921 pour résoudre le problème Adobe Commerce en raison duquel une erreur interne se produit lors de la demande des détails du panier auprès de GraphQL pour un produit configurable en rupture de stock.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 687460c4-f0d5-45d2-82b1-dda2947fe1e7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-52921 : erreur de demande de détails de panier auprès de GraphQL pour un produit configurable en rupture de stock

Le correctif ACSD-52921 corrige le problème d’erreur interne lors de la demande de détails de panier auprès de GraphQL pour un produit configurable en rupture de stock. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.35 est installée. L’ID de correctif est ACSD-52921. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur interne se produit lors de la demande des détails du panier auprès de GraphQL pour un produit configurable en rupture de stock.

<u>Étapes à reproduire</u>:

1. Créez un produit configurable avec quelques options.
1. Ajoutez une option pour le produit configurable ci-dessus dans le panier à partir de l’interface (passage en caisse des invités).
1. Obtenez la variable `[ masked_id ]` de la `[ quote_id_mask ]` table db pour le devis créé ci-dessus.
1. Exécutez la requête GraphQL suivante pour obtenir les détails du panier d’invités ci-dessus.

   Ajoutez la variable `[ masked_id ]` reçu de l’étape 3 de la requête.

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. Cela renverra les détails des guillemets sans problème.
1. Accédez au serveur principal et mettez à jour le *[!UICONTROL Stock Status]* to *[!UICONTROL Out of Stock]*.
1. Exécutez la même requête GraphQL, comme indiqué à l’étape 4.

<u>Résultats attendus</u>:

Le message d’erreur est envoyé/traité correctement dans la réponse.

<u>Résultats réels</u>:

*Serveur interne 500* est générée en réponse à la requête GraphQL.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
