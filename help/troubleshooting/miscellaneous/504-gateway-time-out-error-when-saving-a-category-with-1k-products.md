---
title: Erreur de délai d’expiration de la passerelle 504 lors de l’enregistrement d’une catégorie avec des produits 1k+
description: Cet article suggère une solution au problème de délai d’expiration que vous pourriez rencontrer lors d’opérations avec des catégories volumineuses (1k+ plus produits).
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Erreur de délai d’expiration de la passerelle 504 lors de l’enregistrement d’une catégorie avec des produits 1k+

Cet article suggère une solution au problème de délai d’expiration que vous pourriez rencontrer lors d’opérations avec des catégories volumineuses (1k+ plus produits).

## Produits et versions concernés :

* Adobe Commerce sur l’infrastructure cloud 2.3.3
* Adobe Commerce on-premise 2.3.3
* Magento Open Source 2.3.3

## Problème

Conditions préalables : la **Magasins** > **Configuration** > **CATALOGUE** > **Catalogue** > **Utilisation du chemin d’accès aux catégories pour les URL de produit** est définie sur *Oui* pour la vue de magasin.

<u>Étapes à reproduire</u>

1. Dans l’administrateur de Commerce, accédez à **Catalogue** > **Catégories**.
1. Ouvrez une grande catégorie, comme plus de 1 000 produits attribués.
1. Ajoutez un produit à la catégorie.
1. Cliquez sur **Catégorie d’enregistrement**.

<u>Résultat attendu :</u>

La catégorie a été enregistrée avec succès.

<u>Résultat réel :</u>

Après cinq minutes de processus d’enregistrement, la page 504 gateway timeout error s’affiche.

## Cause

Le processus prend plus de temps que le délai d’expiration configuré du serveur.

## Solution

Désactivation de la variable **Générer des réécritures d’URL &quot;catégorie/produit&quot;** Cette option supprime toutes les réécritures d’URL de catégorie/produit de la base de données et réduit considérablement le temps nécessaire aux opérations avec des catégories volumineuses.

>[!WARNING]
>
>Si vous désactivez cette option, la suppression définitive des réécritures d’URL de catégorie/produit sera supprimée sans possibilité de les restaurer.

Pour désactiver la fonction **Générer des réécritures d’URL &quot;catégorie/produit&quot;** option :

1. Dans l’administrateur de Commerce, accédez à **Magasins** > **Configuration** > **CATALOGUE** > **Catalogue**.
1. Dans le coin supérieur gauche de la page de configuration, dans la **Portée** , définissez votre portée de configuration sur *Configuration par défaut*.
1. Définir **Générer des réécritures d’URL &quot;catégorie/produit&quot;** to *Non*.
1. Cliquez sur **Enregistrer la configuration**.
1. Nettoyer le cache en cours d’exécution    ```bash    bin/magento cache:clean    ```    ou dans l’administrateur Commerce sous **Système** > **Outils** > **Gestion du cache**.

Vous pouvez maintenant ajouter des produits à des catégories ou déplacer des catégories avec un grand nombre de produits. Ces opérations prendront beaucoup moins de temps et ne devraient pas entraîner de délai d’expiration.

## Lecture connexe

[Redirections automatiques de produits](https://docs.magento.com/user-guide/v2.3/marketing/url-redirect-product-automatic.html) dans notre guide d’utilisation.
