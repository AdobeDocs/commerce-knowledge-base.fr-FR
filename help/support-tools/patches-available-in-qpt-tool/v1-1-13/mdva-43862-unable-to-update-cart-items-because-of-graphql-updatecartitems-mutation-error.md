---
title: "MDVA-43862 : le client ne peut pas mettre à jour les articles du panier en raison d’une erreur de mutation GraphQL UpdateCartItems"
description: Le correctif MDVA-43862 résout le problème où le client ne peut pas mettre à jour les articles du panier en raison d’une erreur de mutation GraphQL UpdateCartItems. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 est installé. L’ID de correctif est MDVA-43862. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 5f0a2970-34a8-4a25-baf8-15c007f97084
feature: GraphQL, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43862 : le client ne peut pas mettre à jour les articles du panier en raison d’une erreur de mutation UpdateCartItems de GraphQL

Le correctif MDVA-43862 résout le problème où le client ne peut pas mettre à jour les articles du panier en raison d’une erreur de mutation GraphQL UpdateCartItems. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.13 est installée. L’ID de correctif est MDVA-43862. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1, 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le client ne peut pas mettre à jour les articles du panier en raison d’une erreur de mutation UpdateCartItems de GraphQL.

<u>Étapes à reproduire</u>:

1. Créez un produit configurable (MH01) en attribuant un simple (MH01-XL-Gray).
1. Accédez à Administration Commerce > **Catalogue** > **Produits** > **SKU** > **MH01** > **Options personnalisables**.
1. Ajoutez une option personnalisée au produit.
   * Titre de l’option : Option1
   * Type d’option : Champ
   * Obligatoire : Oui
   * Prix : 10,00
   * Type de prix : fixe
   * SKU : MHC1
   * Nombre max. de caractères : 25
1. Exécutez la requête GraphQL ci-dessous pour générer l’identifiant de panier.

   ```GraphQL
   mutation {
     createEmptyCart
   }
   ```

1. Notez le code d’identifiant de panier.
1. Exécutez la requête ci-dessous pour ajouter un produit configurable au panier :

   ```GraphQL
   mutation {
   addConfigurableProductsToCart(
   input: {
       cart_id: "<cart ID from above step>",
       cart_items: [{
       parent_sku: "MH01",
       data: {
           quantity: 1,
           sku: "MH01-XL-Gray"
           },
           customizable_options: {
               id: 1,
               value_string: "2"
               }
           }
       ]
   }
   )
   {
   cart {
     items {
       uid
       quantity
       product {
         name
         sku
       }
       ... on ConfigurableCartItem {
         configurable_options {
           option_label
         }
       }
     }
   }
   }
   }
   ```

1. Vous remarquerez que le panier est renseigné avec l’élément configurable.
1. Notez l’uid renvoyé.
1. Exécutez à nouveau la requête ci-dessous pour mettre à jour l’élément de panier.

   ```GraphQL
   mutation {
     updateCartItems(
       input: {
         cart_id: "<cart ID from previous step>",
         cart_items: [
           {
             cart_item_uid: "<uid from previous step>"
             quantity: 3,
             customizable_options:[{
                 id: 1,
                 value_string: "67"
             }]
           }
         ]
       }
     ){
       cart {
         items {
           uid
           product {
             name
           }
           quantity
         }
         prices {
           grand_total{
             value
             currency
           }
         }
       }
     }
   }
   ```

1. Observez la réponse.

<u>Résultats attendus</u>:

Le panier est mis à jour sans problème.

<u>Résultats réels</u>:

Vous obtenez l’erreur suivante :

```GraphQL
{
  "errors": [
    {
      "message": "Could not update cart item: You need to choose options for your item.",
      "extensions": {
        "category": "graphql-input"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "updateCartItems"
      ]
    }
  ],
  "data": {
    "updateCartItems": null
  }
}
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
