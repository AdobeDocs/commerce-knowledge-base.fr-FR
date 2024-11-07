---
title: Les utilisateurs ne peuvent pas ajouter de produit au panier si rien n’est sélectionné dans Autoriser les pays
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.4.4 avec PHP 8.1, où les utilisateurs ne peuvent pas ajouter de produits au panier si l’option Autoriser les pays n’est pas sélectionnée.
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Les utilisateurs ne peuvent pas ajouter de produit au panier si rien n’est sélectionné dans Autoriser les pays

Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.4.4 avec PHP 8.1, où les utilisateurs ne peuvent pas ajouter de produits au panier si l’option Autoriser les pays n’est pas sélectionnée.

## Produits et versions concernés

Adobe Commerce 2.4.4 avec PHP 8.1

## Problème

Les utilisateurs ne peuvent pas ajouter de produits au panier si l’option Autoriser les pays n’est pas sélectionnée.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur Commerce.
1. Accédez à **Magasin** > **Configuration** > **Général** > **Options de pays**
1. Désélectionnez toutes les options du champ **Autoriser les pays** .
1. Cliquez sur **Enregistrer la configuration** pour enregistrer la configuration.
1. Positionnez-vous sur le storefront et essayez d&#39;ajouter un produit au panier.

<u>Résultat attendu :</u>

Vous pouvez ajouter un produit au panier.

<u>Résultat réel :</u>

Vous ne pouvez pas ajouter de produit au panier. L’erreur de console suivante s’affiche :

```bash
Failed to load resource: the server responded with a status of 400 (Bad Request)
customer-data.js:87 Uncaught Error: [object Object]
    at Object.<anonymous> (customer-data.js:87:23)
    at fire (jquery.js:3500:50)
    at Object.fireWith [as rejectWith] (jquery.js:3630:29)
    at done (jquery.js:9798:30)
    at XMLHttpRequest.<anonymous> (jquery.js:10057:37)
```

## Cause

La configuration Adobe Commerce récupère `null` si une configuration à sélection multiple ne comporte aucun élément sélectionné. Cette configuration si elle est traitée avec succès dans des versions PHP antérieures à la version 8.1. Cependant, en PHP 8.1, cela ne fonctionne pas correctement en raison des erreurs provoquées par &quot;[Deprecate pass null to non-nullable arguments of internal fonctions in PHP 8.1](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg)&quot;.

## Solutions

Pour résoudre ce problème, appliquez le correctif suivant :

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## Comment appliquer le correctif

Pour obtenir des instructions, reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.

## Liens utiles

[Appliquez des correctifs personnalisés à Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.
