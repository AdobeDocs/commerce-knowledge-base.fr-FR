---
title: "MDVA-44505 : la requête GraphQL pour le panier en appliquant des points de récompense ne met pas à jour le total général"
description: Le correctif MDVA-44505 résout le problème en raison duquel la requête GraphQL pour un panier appliquant des points de récompense ne prend pas en compte les points de récompense et renvoie un total général incorrect. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID de correctif est MDVA-44505. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: 724273ba-b020-4dba-88ae-94968bbd83de
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44505 : la requête GraphQL pour l’application d’un panier de points de récompense ne met pas à jour le total général

Le correctif MDVA-44505 résout le problème en raison duquel la requête GraphQL pour un panier appliquant des points de récompense ne prend pas en compte les points de récompense et renvoie un total général incorrect. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID de correctif est MDVA-44505. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête GraphQL pour un panier qui applique des points de récompense ne prend pas en compte les points de récompense et renvoie un total général incorrect.

<u>Étapes à reproduire</u> :

1. Configurer les points de récompense.
1. Créez un panier et appliquez quelques points de récompense.
1. Appelez la requête `GetCart` à partir du point d’entrée `GraphQL` et récupérez votre panier :

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. Vérifiez le total général de l’entrée.
1. Vérifiez maintenant le total du panier du client à l’aide de l’API REST (`/rest/V1/carts/mine/totals`).

<u>Résultats attendus</u> :

La requête GraphQL pour le panier renvoie le total général correct qui prend en compte les points de récompense.

<u>Résultats réels</u> :

La requête GraphQL ne prend pas en compte les points de récompense et renvoie un total général incorrect.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
