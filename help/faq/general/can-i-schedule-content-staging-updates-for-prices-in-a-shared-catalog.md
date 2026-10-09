---
title: Puis-je planifier des mises à jour d’évaluation de contenu pour les prix dans un catalogue partagé ?
description: Adobe Commerce ne permet pas de planifier une mise à jour de prix ([Content Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=fr)) pour un ou plusieurs produits d’un catalogue partagé.
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%
---
# Puis-je planifier des mises à jour d’évaluation de contenu pour les prix dans un catalogue partagé ?

Adobe Commerce ne permet pas de planifier une mise à jour de prix ([évaluation de contenu](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=fr)) pour un ou plusieurs produits d’un catalogue partagé.

Cela signifie que vous ne pouvez pas planifier une telle mise à jour des prix directement à partir du menu **Définir la tarification et la structure** du panneau d’administration de Commerce (ce menu ne contient pas de bouton **Planifier une nouvelle mise à jour**).

Néanmoins, vous pouvez utiliser d&#39;autres méthodes et planifier une mise à jour de prix pour :

* un groupe de clients
* prix de base du produit

## Planifier la mise à jour des prix pour un groupe de clients

1. Commencez [planification d’une nouvelle mise à jour du produit](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html?lang=fr).
1. Faites défiler jusqu’au champ **Prix** et cliquez sur **Tarification avancée**.

   ![advanced_pricing.png](assets/advanced_pricing.png){width="600"}

1. Dans la section **Prix du groupe client**, sélectionnez le groupe client nécessaire et définissez le prix mis à jour.

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. Terminez la planification de la mise à jour comme d’habitude.

Dans ce workflow, vous ne pouvez mettre à jour le prix que d’un seul produit ; la mise à jour du prix en masse n’est pas disponible.

Rappel : les catalogues partagés exploitent la tarification du groupe de clients.

**Documentation connexe**

* [Planification d’une mise à jour (évaluation du contenu)](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html?lang=fr) dans notre guide de l’utilisateur.
* [Tarification avancée](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html?lang=fr) dans notre guide de l&#39;utilisateur.

## Planifier la mise à jour des prix pour le prix de base

Voir l’article connexe : [Comment la modification du prix de base affecte-t-elle le prix catalogue partagé ?](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) dans notre base de connaissances de support.
