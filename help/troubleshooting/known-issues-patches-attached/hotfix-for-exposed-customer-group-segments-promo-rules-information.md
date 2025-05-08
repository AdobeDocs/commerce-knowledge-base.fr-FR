---
title: Noms de groupes de clients, segments et informations sur les règles promotionnelles exposés via  [!DNL GraphQL]
description: Cet article fournit un correctif pour empêcher que les noms de groupes de clients, les segments de clients et les informations sur les règles promotionnelles soient divulgués via  [!DNL GraphQL].
feature: GraphQL
role: Admin, Developer
source-git-commit: f32085c80c9dbce513dad15ebf5f77a0e6398466
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Noms de groupes de clients, segments et informations sur les règles promotionnelles exposés via [!DNL GraphQL]

Cet article fournit un correctif pour empêcher que les noms de groupes de clients, les segments de clients et les informations sur les règles promotionnelles soient divulgués via [!DNL GraphQL]. Le problème devrait être résolu dans Adobe Commerce 2.4.8-p1.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

## Problème

Par [!UICONTROL Storefront Personalization Drop-ins], de nouvelles mutations de [!DNL GraphQL] ont été introduites pour afficher des informations de base telles que les noms de groupes de clients, les segments, le panier et les règles de catalogue. Cependant, cela peut exposer des données sensibles telles que des détails d’offre ou des codes de coupon, s’ils sont inclus dans les noms.

### Procédure à suivre

#### Cas I : [!UICONTROL Catalog Rule]

1. Dans la barre latérale *Admin*, accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Définissez les conditions de la règle (par exemple, l’attribut de produit ou la catégorie).
1. Enregistrez et appliquez la règle.
1. Assurez-vous qu’un produit répond aux conditions de la règle.
1. Exécutez la requête [!DNL GraphQL] suivante pour récupérer toutes les règles :

   ```
   query {
       allCatalogRules {
           name
       }
   }
   ```

1. Interroger un produit pour vérifier si la règle s’applique :

   ```
   query {
       products(filter: { sku: { eq: "product-sku" } }) {
           items {
               name
               rules {
                   name
               }
           }
       }
   }
   ```

#### Cas II : [!UICONTROL Cart Rule]

1. Dans la barre latérale *Admin*, accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Définissez des conditions telles que la valeur minimale du panier et le groupe de clients.
1. Enregistrez et appliquez la règle.
1. Ajoutez des produits au panier pour déclencher la règle.
1. Utilisez [!DNL GraphQL] pour vérifier toutes les règles du panier :

   ```
   query {
       allCartRules {
           name
       }
   }
   ```

1. Vérifiez si les règles sont appliquées au panier actif :

   ```
   query {
       cart(cart_id: "your-cart-id") {
           rules {
               name
           }
       }
   }
   ```

#### Cas III : [!UICONTROL Customer Group]

1. Dans la barre latérale *Admin*, accédez à **[!UICONTROL Customers]** > **[!UICONTROL Customer Groups]**.
1. Vérifiez que les groupes attendus existent.
1. Utilisez [!DNL GraphQL] pour récupérer tous les groupes :

   ```
   query {
       allCustomerGroups {
           name
       }
   }
   ```

1. Vérifier le groupe du client/invité :

   ```
   query {
       customerGroup {
           name
       }
   }
   ```

#### Cas IV : [!UICONTROL Customer Segment] (pour Adobe Commerce uniquement)

1. Dans la barre latérale *Admin*, accédez à **[!UICONTROL Customers]** > **[!UICONTROL Customer Segments]** → **[!UICONTROL Add Segment]**.
1. Définissez des conditions basées sur le client (par exemple, le contenu de la commande ou du panier).
1. Attribuez la portée applicable : *[!UICONTROL Visitor]*, *[!UICONTROL Registered]* ou les deux.
1. Assurez-vous que les conditions correspondent à un client ou une cliente de test.
1. Utilisez [!DNL GraphQL] pour vérifier tous les segments :

   ```
   query {
       allCustomerSegments {
           name
           apply_to
       }
   }
   ```

1. Validez les segments appliqués à un panier :

   ```
   query {
       customerSegments(cartId: "your-cart-id") {
           name
       }
   }
   ```

<u>Résultat attendu </u> :

Les noms des groupes de clients, les segments et les informations des règles promotionnelles ne sont pas exposés via [!DNL GraphQL].

<u>Résultat réel</u> :

Les noms des groupes de clients, des segments et des informations sur les règles promotionnelles sont exposés via [!DNL GraphQL].

## Solution

Appliquez les correctifs ci-joints en fonction de votre version d’Adobe Commerce :

* Pour Adobe Commerce version 2.4.8 :

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
   * [LYNX-839_EE_2.4.8.patch](assets/LYNX-839_EE_2.4.8.patch.zip)

* Pour [!DNL Magento] Open Source version 2.4.8 :

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
