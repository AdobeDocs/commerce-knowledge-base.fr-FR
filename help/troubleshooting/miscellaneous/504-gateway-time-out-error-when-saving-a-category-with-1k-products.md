---
title: Erreur de délai d’expiration de la passerelle 504 lors de l’enregistrement d’une catégorie avec des produits 1k+
description: Cet article suggère une solution au problème de délai d’expiration que vous pourriez rencontrer lors d’opérations avec des catégories volumineuses (1k+ plus produits).
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Conditions préalables : l’option **Magasins** > **Configuration** > **CATALOG** > **Catalogue** > **Utiliser le chemin des catégories pour les URL de produit** est définie sur *Oui* pour la vue de magasin.

<u>Étapes à reproduire</u>

1. Dans l’administrateur Commerce, accédez à **Catalogue** > **Catégories**.
1. Ouvrez une grande catégorie, comme plus de 1 000 produits attribués.
1. Ajoutez un produit à la catégorie.
1. Cliquez sur **Enregistrer la catégorie**.

<u>Résultat attendu :</u>

La catégorie a été enregistrée avec succès.

<u>Résultat réel :</u>

Après cinq minutes de processus d’enregistrement, la page 504 gateway timeout error s’affiche.

## Cause

Le processus prend plus de temps que le délai d’expiration configuré du serveur.

## Solution

La désactivation de l’option **Générer l’URL &quot;de catégorie/produit&quot; réécrit** supprimera toutes les réécritures d’URL de catégorie/produit de la base de données et réduira considérablement le temps nécessaire aux opérations avec de grandes catégories.

>[!WARNING]
>
>Si vous désactivez cette option, la suppression définitive des réécritures d’URL de catégorie/produit sera supprimée sans possibilité de les restaurer.

Pour désactiver l&#39;option **Generate &quot;category/product&quot; URL Rewrites** :

1. Dans l’administrateur Commerce, accédez à **Magasins** > **Configuration** > **CATALOGUE** > **Catalogue**.
1. Dans le coin supérieur gauche de la page de configuration, dans le champ **Portée**, définissez votre portée de configuration sur *Configuration par défaut*.
1. Définissez **Générer l’URL &quot;catégorie/produit&quot; de réécritures** sur *Non*.
1. Cliquez sur **Enregistrer la configuration**.
1. Nettoyer le cache en cours d’exécution    ```bash    bin/magento cache:clean    ```    ou dans l’administrateur Commerce sous **System** > **Tools** > **Cache Management**.

Vous pouvez maintenant ajouter des produits à des catégories ou déplacer des catégories avec un grand nombre de produits. Ces opérations prendront beaucoup moins de temps et ne devraient pas entraîner de délai d’expiration.

## Lecture connexe

[Redirections automatiques des produits](https://experienceleague.adobe.com/fr/docs/commerce-admin/marketing/seo/url-rewrites/url-redirect-product-automatic) dans notre guide d’utilisation.
