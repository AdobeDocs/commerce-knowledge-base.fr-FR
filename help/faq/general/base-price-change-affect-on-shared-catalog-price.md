---
title: Incidence de la modification du prix de base sur le prix catalogue partagé
description: 'Cet article répond à la question suivante : si un produit d''un catalogue partagé a un prix personnalisé et que le prix de base du produit change (par exemple après une mise à jour planifiée), quel prix s''applique dans le catalogue partagé ?'
exl-id: 916678c1-ada6-4f23-af16-b107cb83ff16
feature: Catalog Management
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Incidence de la modification du prix de base sur le prix catalogue partagé

Cet article répond à la question suivante : si un produit d&#39;un catalogue partagé a un prix personnalisé et que le prix de base du produit change (par exemple après une mise à jour planifiée), quel prix s&#39;applique dans le catalogue partagé ?

## Lorsque le prix personnalisé est défini sur Pourcentage, le prix du catalogue partagé change également

Si le prix personnalisé d’un produit dans un catalogue partagé a été défini sur Pourcentage, le prix du catalogue partagé du produit est implicitement mis à jour après la modification du prix de base.

En d’autres termes, lorsque le prix de base est mis à jour (par le biais d’une mise à jour normale ou planifiée), le prix du catalogue partagé change également après l’application du pourcentage de remise.

## Lorsque le prix personnalisé est défini sur Fixe, le prix du catalogue partagé ne change pas

Si le prix personnalisé d’un produit dans un catalogue partagé a été défini sur Fixe, le prix dans le catalogue partagé ne change jamais, quelle que soit la manière dont nous mettons à jour le prix de base (par le biais d’une mise à jour planifiée, d’Adobe Commerce Admin, de l’API ou d’un import).

## Storefront affiche toujours le prix disponible le plus bas

Si le prix de base du produit change et devient inférieur au prix catalogue partagé correspondant, le Storefront affiche le prix de base comme le prix le plus bas disponible dans le système.

## Lecture connexe

[Définissez la tarification et la structure d’un catalogue partagé](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/define/catalog-shared-pricing-structure.html) dans notre guide de l’utilisateur.
