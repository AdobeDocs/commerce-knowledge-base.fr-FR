---
title: Adobe Commerce invite les clients à se connecter à un lien non valide
description: L’article fournit un lien vers le correctif pour un problème connu d’Adobe Commerce 2.3.5, où les clients sont invités à se connecter, mais le lien de renvoi d’un email de confirmation ne fonctionne pas.
exl-id: 8adef44f-56a6-4f57-a9b5-fb8583d8ae8d
feature: Logs
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce invite les clients à se connecter à un lien non valide

L’article fournit un lien vers le correctif pour un problème connu d’Adobe Commerce 2.3.5, où les clients sont invités à se connecter, mais le lien de renvoi d’un email de confirmation ne fonctionne pas.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5

## Problème

Adobe Commerce invite les clients à se connecter en affichant ce message : *&quot;Ce compte n&#39;est pas confirmé. Cliquez ici pour renvoyer l&#39;email de confirmation&quot;*. La variable **Cliquez ici** Le lien doit ouvrir la page Envoyer le lien de confirmation , mais il est inactif.

## Solution

Un correctif pour ce problème est disponible dans les ressources techniques d’Adobe Commerce : [Correctif du problème de lien email de confirmation de compte pour Adobe Commerce 2.3.5](https://magento.com/tech-resources/download?_ga=2.193540264.409362045.1590506265-807369446.1578680711#download2368). Un correctif permanent sera disponible dans Adobe Commerce 2.3.6, dont la sortie est prévue au 4e trimestre 2020.

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions sur la façon d’appliquer un correctif de compositeur.

## Lecture connexe

Articles de notre base de connaissances d’assistance et de la documentation destinée aux développeurs pour les problèmes connus d’Adobe Commerce 2.3.5 :

* [Problème connu d’Adobe Commerce 2.3.5 : commandes multi-produits virtuelles](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
* [Problème connu de la comparaison de produits dans Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Correctif Adobe Commerce 2.3.5, 2.3.5-p1 : problème de paiement du pays](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Adobe Commerce invite les clients à se connecter à un lien non valide](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Problème connu du comptage de produit d’action en bloc dans Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Correctif du problème de paiement Amazon dans Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
* [Problèmes connus d’Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
