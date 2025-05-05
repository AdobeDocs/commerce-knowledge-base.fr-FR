---
title: Puis-je planifier des mises à jour d’évaluation de contenu pour les prix dans un catalogue partagé ?
description: Adobe Commerce ne propose pas la fonctionnalité de planification d’une mise à jour de prix ([Évaluation du contenu](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=fr)) pour un ou plusieurs produits dans un catalogue partagé.
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
source-git-commit: c3120f7df24e105b082df6544ab82241d6b6851f
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Puis-je planifier des mises à jour d’évaluation de contenu pour les prix dans un catalogue partagé ?

Adobe Commerce n’offre pas la fonctionnalité de planification d’une mise à jour de prix ([Content Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=fr)) pour un ou plusieurs produits dans un catalogue partagé.

Cela signifie que vous ne pouvez pas planifier une telle mise à jour de prix directement à partir du menu **Définir les tarifs et la structure** du panneau d’administration de Commerce (il n’y a pas de bouton **Planifier une nouvelle mise à jour** dans ce menu).

Néanmoins, vous pouvez utiliser d’autres méthodes et planifier une mise à jour du prix pour :

* un groupe de clients ;
* le prix de base du produit

## Planifier la mise à jour du prix pour un groupe de clients

1. Commencez [à planifier une nouvelle mise à jour de produit](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html?lang=fr).
1. Faites défiler l’écran jusqu’au champ **Price** et cliquez sur **Advanced PrTarification**.

   ![advanced_price.png](assets/advanced_pricing.png){width="600"}

1. Dans la **section Prix du groupe client**, sélectionnez le groupe client nécessaire et définissez le prix mis à jour.

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. Terminez la planification de la mise à jour comme vous le faites habituellement.

Dans ce workflow, vous ne pouvez mettre à jour que le prix d’un seul produit ; la mise à jour du prix en bloc n’est pas disponible.

Rappel : les catalogues partagés tirent parti des tarifs des groupes de clients.

**Documentation connexe**

* [Planification d’une mise à jour (évaluation de contenu)](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html?lang=fr) dans notre guide d’utilisation.
* [Advanced Tarification](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html?lang=fr) dans notre guide d’utilisation.

## Planifier la mise à jour du prix de base

Voir l’article connexe : [Quel est l’impact de la modification du prix de base sur le prix du catalogue partagé ?](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) dans notre base de connaissances d’assistance.
