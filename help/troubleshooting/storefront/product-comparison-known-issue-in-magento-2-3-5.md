---
title: Problème connu de la comparaison de produits dans Adobe Commerce 2.3.5
description: Cet article fournit des recommandations sur la manière d’éviter un problème connu de [comparaison de produits](https://docs.magento.com/user-guide/marketing/product-compare.html) dans Adobe Commerce on-premise 2.3.5 et Adobe Commerce on cloud infrastructure 2.3.5.
exl-id: 1488e2db-4a5d-4963-b48e-b84f760582d1
feature: Products, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Problème connu de la comparaison de produits dans Adobe Commerce 2.3.5

Cet article fournit des recommandations sur la manière d’éviter un événement connu [comparaison de produits](https://docs.magento.com/user-guide/marketing/product-compare.html) Problème dans Adobe Commerce on-premise 2.3.5 et Adobe Commerce sur l’infrastructure cloud 2.3.5.

## Produits et versions concernés

* Adobe Commerce on-premise 2.3.5
* Adobe Commerce sur l’infrastructure cloud 2.3.5

## Problème

Lorsqu’un utilisateur tente de comparer des produits provenant de différentes consultations de magasin et qu’un produit a une valeur vide pour un attribut comparable, Adobe Commerce affiche une page de comparaison des produits corrompue.

## Solution

Spécifiez des valeurs non vides pour des attributs de produit comparables ou utilisez la valeur de vue de magasin par défaut pour l’attribut . Les valeurs d’attribut comparables ne peuvent pas être vides.

>[!NOTE]
>
>Les attributs de produit doivent être utilisés pour la comparaison à l’aide de la variable **Comparable sur Storefront** paramètre de configuration . Pour plus d’informations, voir la section [Création d’attributs de produit](https://docs.magento.com/user-guide/stores/attribute-product-create.html#step-4-describe-the-storefront-properties) dans notre guide d’utilisation.

Un correctif sera disponible dans Adobe Commerce 2.3.6, dont la sortie est prévue au quatrième trimestre 2020.

Vous pouvez afficher le correctif dans GitHub (veuillez tenir compte du fait que le correctif n’a pas fait l’objet de tests de régression et qu’il ne s’agit pas d’un correctif officiel) : <https://github.com/magento/magento2/pull/27662>

## Lecture connexe

<ul><li>Articles de la base de connaissances de la prise en charge d’Adobe Commerce pour les problèmes connus d’Adobe Commerce 2.3.5 :<ul>
<li>
<p title="Commandes multi-expédition avec un produit virtuel non traité correctement dans Adobe Commerce 2.3.5"><a href="/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md">Commandes multi-expédition avec un produit virtuel non traité correctement dans Adobe Commerce 2.3.5</a></p>
</li>
<li><a href="/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md">Problème connu du comptage de produit d’action en bloc dans Adobe Commerce 2.3.5</a></li>
<li>
<p title="Problème lié au mode de paiement par pays dans Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.5 et 2.3.5-p1"><a href="/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md">Problème lié au mode de paiement par pays dans Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.5 et 2.3.5-p1</a></p>
</li>
<li>
<p title="Adobe Commerce invite les clients à se connecter, mais fournit un lien non valide"><a href="/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md">Adobe Commerce invite les clients à se connecter, mais fournit un lien non valide</a></p>
</li>
<li>
<p title="Correctif du problème de paiement Amazon dans Adobe Commerce 2.3.5-p1"><a href="/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md">Correctif du problème de paiement Amazon dans Adobe Commerce 2.3.5-p1</a></p>
</li>
</ul>
</li><li><a href="https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues">Problèmes connus d’Adobe Commerce 2.3.5</a> dans notre documentation destinée aux développeurs</li></ul>
