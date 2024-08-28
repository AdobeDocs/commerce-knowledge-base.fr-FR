---
title: "ACSD-57643 : produits avec des options personnalisées ajoutées incorrectement au panier via GraphQL"
description: Appliquez le correctif ACSD-57643 pour résoudre le problème Adobe Commerce en raison duquel les produits avec des options personnalisées sont incorrectement ajoutés au panier via GraphQL.
feature: Shopping Cart, GraphQL, Products
role: Admin, Developer
source-git-commit: 62c83f36440cd05fa2d7f85da3e22c9744ad75c1
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# ACSD-57643 : produits avec des options personnalisées ajoutées incorrectement au panier via GraphQL

Le correctif ACSD-57643 corrige le problème en raison duquel les produits avec des options personnalisées sont ajoutés incorrectement au panier via GraphQL. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 est installé. L’ID de correctif est ACSD-57643. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec Adobe Commerce et les versions de Magento Open Source :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits avec des options personnalisées sont incorrectement ajoutés au panier via GraphQL.

<u>Étapes à reproduire</u> :

1. Créez un champ de type d’option personnalisé pour le produit.
1. Générez un jeton client à l’aide de GraphQL.
1. Créez un panier vide.
1. Ajoutez le produit au panier à l’aide de la payload suivante :

   ```graphql
   mutation {
     addProductsToCart(
       cartId: "wNVOTaE6sDCJoObZCCqikHQI3GyFaVif"
       cartItems: [
         {
           quantity: 1
           sku: "24-MB01"
           entered_options: [{
             uid:"Y3VzdG9tLW9wdGlvbi8x",
             value:"product1 option1 "
           }]
         },
         {
           quantity: 1
           sku: "24-MB01"
           entered_options: [{
             uid:"Y3VzdG9tLW9wdGlvbi8x",
             value:"product2 option1"
           }]
         }
         {
           quantity: 3
           sku: "24-MB01",
           entered_options: [{
             uid:"Y3VzdG9tLW9wdGlvbi8x"
             value:"product3 option1"
           }]        
         }
       ]
     ) {
       cart {
         items {
           product {
             name
             sku
           }
           ... on SimpleCartItem {
             customizable_options {
               customizable_option_uid
               label
               values {
                 customizable_option_value_uid
                 value
               }
             }
           }
           quantity
         }
       }
       user_errors {
         code
         message
       }
     }
   }
   ```

1. Vous constaterez que le produit n’est ajouté qu’une seule fois :

   ```json
   {
     "data": {
       "addProductsToCart": {
         "cart": {
           "items": [
             {
               "product": {
                 "name": "Joust Duffle Bag",
                 "sku": "24-MB01"
               },
               "customizable_options": [
                 {
                   "customizable_option_uid": "Y3VzdG9tLW9wdGlvbi8x",
                   "label": "Option1",
                   "values": [
                     {
                       "customizable_option_value_uid": "Y3VzdG9tLW9wdGlvbi8x",
                       "value": "product1 option1"
                     }
                   ]
                 }
               ],
               "quantity": 5
             }
           ]
         },
         "user_errors": []
       }
     }
   }
   ```

<u>Résultats attendus</u> :

Un produit peut être ajouté au panier à l’aide de différentes options personnalisées pour le même SKU simultanément.

<u>Résultats réels</u> :

Impossible d’ajouter un produit au panier à l’aide de différentes options personnalisées pour le même SKU simultanément.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].