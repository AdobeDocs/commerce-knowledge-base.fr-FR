---
title: Échec de l’importation des informations de produit CSV pour le même nom
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.3 lié à l’obtention d’erreurs lors de l’importation d’un fichier `.csv` avec des informations sur les produits s’il existe des produits portant le même nom.
exl-id: 420b0283-455a-4bd5-ba51-18f341ddacd5
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Échec de l’importation des informations de produit CSV pour le même nom

Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.3 lié à l’obtention d’erreurs lors de l’importation d’un fichier `.csv` avec des informations sur les produits s’il existe des produits portant le même nom.

## Problème

Lorsqu&#39;un fichier `.csv` contenant des informations sur les produits est importé et qu&#39;il existe des produits portant le même nom, l&#39;erreur suivante s&#39;affiche à l&#39;étape Vérifier les données : *&quot;`URL Key XYZ was already generated for an item with the SKU %sku%"`*. Le problème est dû à la réécriture des URL des produits lors de l’importation, même lorsqu’il n’y a pas de colonne pour les URL des produits dans le fichier `.csv` importé.

<u>Étapes à reproduire</u> :

1. Créez deux produits configurables portant le même nom dans l’administrateur Commerce.
1. Créez un fichier `.csv` pour importer des données pour ces produits, qui contient par exemple les colonnes suivantes : `sku` | `product_type` | `name` | `product_websites` | `store_view_code`
1. Accédez à **System** > **Data Transfer** > **Import** et sélectionnez le fichier `.csv`.
1. Cliquez sur **Vérifier les données**.

<u>Résultat attendu</u> :

Aucun problème n’a été détecté. Vous pouvez importer le fichier `.csv` avec succès.

<u>Résultat réel</u> :

Le message d’erreur suivant s’affiche : *&quot;URL Key XYZ a déjà été généré pour un élément avec le SKU %sku%&quot;*. Il n’est pas possible d’importer le fichier.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier ou cliquez sur le lien suivant :

[Téléchargez MDVA-12899\_EE\_2.2.3\_COMPOSER\_v2.patch.](assets/MDVA-12899_EE_2.2.3_COMPOSER_v2.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce on-premise 2.2.3

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les éditions et versions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud de la version 2.2.0 à la version 2.2.7 et 2.3.0
* Adobe Commerce sur site de la version 2.2.0 à la version 2.2.2, de la version 2.2.4 à la version 2.2.7 et la version 2.3.0

## Comment appliquer le correctif

Pour obtenir des instructions, reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.

## Liens utiles

[Application de correctifs personnalisés à Adobe Commerce sur l’infrastructure cloud](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)

## Fichiers attachés
