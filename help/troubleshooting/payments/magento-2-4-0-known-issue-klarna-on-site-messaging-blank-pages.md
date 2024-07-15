---
title: "Problème connu d’Adobe Commerce 2.4.0 : pages vierges de messagerie sur site Klarna"
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.0 avec le mode de paiement Klarna, en raison duquel l’activation de la messagerie Klarna sur site sans spécifier de thème de conception n’affichait pas correctement les pages de produit sur le storefront (les pages de produit apparaissent vides).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Problème connu d’Adobe Commerce 2.4.0 : pages vierges de messagerie sur site Klarna

Cet article décrit un problème connu d’Adobe Commerce 2.4.0 avec le mode de paiement Klarna, en raison duquel l’activation de la messagerie Klarna sur site sans spécifier de thème de conception n’affichait pas correctement les pages de produit sur le storefront (les pages de produit apparaissent vides).

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

<u>Conditions préalables :</u> le mode de paiement Klarna est activé.

<u>Étapes à reproduire :</u>

1. Dans l’administrateur Commerce, accédez à **Magasins** > **Configuration** > **Ventes** > **Méthodes de paiement** > **Klarna** > **Messagerie sur site Klarna**.
1. Définissez **Activer** sur *Oui*.
1. Laissez vide le champ **Thème de conception**.
1. Enregistrez la configuration en cliquant sur **Enregistrer la configuration**.
1. Accédez à storefront et à n’importe quelle page de produit.

<u>Résultat attendu :</u>

La page se charge correctement avec le thème de conception par défaut appliqué pour la messagerie Klarna sur site.

<u>Résultat réel :</u>

Une page vierge s’affiche.

## Solution

Si vous activez la messagerie Klarna sur site, assurez-vous toujours que le champ **Thème de conception** n’est pas vide.
