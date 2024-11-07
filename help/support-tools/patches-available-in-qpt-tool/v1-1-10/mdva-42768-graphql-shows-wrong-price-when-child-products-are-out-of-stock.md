---
title: 'MDVA-42768 : GraphQL affiche un mauvais prix lorsque les produits pour enfants sont en rupture de stock'
description: Le correctif MDVA-42768 corrige le problème en raison duquel GraphQL affiche le mauvais prix lorsque les produits enfants configurables sont en rupture de stock. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 est installé. L’ID de correctif est MDVA-42768. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 012e7e21-e508-4449-98a6-4bdb41284c3a
feature: GraphQL, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# MDVA-42768 : GraphQL affiche un mauvais prix lorsque les produits pour enfants sont en rupture de stock.

Le correctif MDVA-42768 corrige le problème en raison duquel GraphQL affiche le mauvais prix lorsque les produits enfants configurables sont en rupture de stock. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 est installé. L’ID de correctif est MDVA-42768. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque les produits enfants d’un produit configurable sont en rupture de stock et que le paramètre Afficher les produits en rupture de stock est activé, la requête GraphQL affiche le prix normal du produit comme **0**.

<u>Conditions préalables</u> :

Des exemples de données sont installés.

<u>Étapes à reproduire</u> :

1. Activez le paramètre d’affichage des produits en rupture de stock dans l’administrateur Commerce en accédant à **Magasins** > **Configuration** > **Catalogue** > **Inventaire**.
1. Créez un produit configurable et affectez-lui un produit enfant simple.
1. Définissez l’inventaire de la variante (simple) du produit sur **Out of Stock**.
1. Réindexation.
1. Exécutez la requête GraphQL ci-dessous :

   ```GraphQL
   query {
     products(filter: { sku: { eq: "MH01" } }) {
       items {
         sku
         price_range {
           minimum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
           maximum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
         }
       }
     }
   }
   ```

1. Vérifiez la section de réponse `minimum_price` > `regular price`.

<u>Résultats attendus</u> :

Le prix normal minimum n’est pas affiché comme 0 en réponse.

<u>Résultats réels</u> :

Prix normal minimum = 0 en réponse.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
