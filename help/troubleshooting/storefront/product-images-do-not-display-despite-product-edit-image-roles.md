---
title: Les images de produit ne s’affichent pas en dépit des rôles d’image de modification de produit
description: Cet article fournit un correctif lorsque les images de produit ne s’affichent pas sur votre vitrine, en dépit des rôles d’image définis sur la page de modification du produit.
exl-id: 456baa5a-fa16-4bc1-9d6c-54106fae58ca
feature: Cache, Products, Roles/Permissions, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Les images de produit ne s’affichent pas en dépit des rôles d’image de modification de produit

Cet article fournit un correctif lorsque les images de produit ne s’affichent pas sur votre vitrine, en dépit des rôles d’image définis sur la page de modification du produit.

**Cause :** sur les instances Adobe Commerce comportant plusieurs magasins, certaines images de produit peuvent avoir les valeurs `no_selection` pour les attributs de rôle d’image `image`, `small_image`, `thumbnail`, `swatch`. Ces valeurs `no_selection` apparaissent lorsque le rôle d’image de produit est défini sur la portée globale de toutes les boutiques au lieu de la portée d’un magasin particulier (en d’autres termes, sur les **vues de toutes les boutiques** au lieu d’une **vue de magasin** spécifique). Pour savoir si c’est votre cas, exécutez le script SQL de la section **Cause** ci-dessous.

**Solution :** supprimez les lignes avec les valeurs `no_selection` pour ces images à l’aide du script SQL de la section Solution ci-dessous.

## Versions affectées

* Adobe Commerce On-Premise 2.X.X
* Adobe Commerce sur l’infrastructure cloud 2.X.X

## Problème

Les images de produit peuvent ne pas s’afficher sur votre vitrine, bien que les rôles d’image (Base, Petit, Miniature, Échantillon) aient été correctement définis sur la page Produit du panneau d’administration.

Lorsque vous cochez la page Produit avec la **Vue du magasin** définie sur **Toutes les vues du magasin**, les rôles sont définis sur l’écran **Détails de l’image**.

![all_store_views.png](assets/all_store_views.png)

![image_rôles.png](assets/image_roles.png)

Cependant, sur le storefront, l’image ne s’affiche pas ; lorsque vous consultez la page Produit au niveau du magasin spécifique (en changeant la **vue Boutique**), l’image est là, mais les rôles ne sont pas définis.

![image_rôles_not_set.png](assets/image_roles_not_set.png)

## Cause

Sur les instances Adobe Commerce multi-magasin (avec plusieurs magasins), certaines images de produit peuvent avoir les valeurs `no_selection` pour les attributs `image`, `small_image`, `thumbnail` et `swatch` (ces attributs correspondent à des rôles d’image). Ces valeurs `no_selection` apparaissent lorsque le rôle d’image de produit est défini sur la portée globale de toutes les boutiques au lieu de la portée d’un magasin particulier (en d’autres termes, sur les **vues de toutes les boutiques** au lieu d’une **vue de magasin** spécifique).

Techniquement parlant : sur `store_id=0` (qui contient les paramètres globaux pour tous les magasins sur votre instance Adobe Commerce), les rôles d’image de produit peuvent être définis : cela signifie que les attributs `image`, `small_image`, `thumbnail` et `swatch` ont des valeurs valides (chemin d’accès aux images). En même temps, sur `store_id=1` (qui est une représentation de magasin spécifique), les valeurs de ces attributs sont `no_selection`.

### Comment vérifier que c&#39;est votre problème

Exécutez cette requête SQL :

```sql
SELECT `cpev_s`.*, `cpev_0`.`value` AS `store_value` FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

Si la requête renvoie un résultat comme ci-dessous, vous traitez le problème documenté dans cet article :

```sql
+----------+--------------+----------+--------+--------------+----------------------------+
| value_id | attribute_id | store_id | row_id | value        | store_value                |
+----------+--------------+----------+--------+--------------+----------------------------+
|    67722 |           87 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67723 |           88 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67724 |           89 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67814 |           87 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6769 |           87 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67815 |           88 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6770 |           88 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67816 |           89 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6771 |           89 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
+----------+--------------+----------+--------+--------------+----------------------------+
9 rows in set (0.06 sec)
```

### Pourquoi cela arrive-t-il ?

Si l’application Adobe Commerce possède plusieurs magasins, il se peut qu’elle ne synchronise pas les données entre un magasin particulier et les paramètres du magasin global.

Les valeurs sur `store_id=1` ont plus de priorité que le magasin par défaut (global) (`store_id=0`). Par conséquent, l’application peut ignorer les paramètres d’image globaux et utiliser la configuration de l’étendue de magasin (`no_selection` pour les attributs de rôle d’image) lors de l’affichage d’une image.

## Solution {#solution}

Supprimez les attributs avec les valeurs `no_selection` à l’aide de ce script SQL :

```
DELETE `cpev_s`.* FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

Une fois ces attributs supprimés, les rôles de magasins spécifiques sont définis et les images s’affichent sur le storefront.

## Informations supplémentaires

Vous ne pourrez pas voir les résultats de la correction immédiatement si le cache de page complète est activé dans votre instance Adobe Commerce.

Pour que les modifications s’affichent, actualisez le cache de page à l’aide du menu **Gestion du cache** de votre panneau d’administration.

## Informations supplémentaires

### Magasins et portées

[Magasins et portées de magasin](/docs/commerce-admin/stores-sales/site-store/stores.html) dans notre guide d’utilisation

### Images

[Téléchargement des images de produit](/docs/commerce-admin/catalog/products/digital-assets/product-image.html#upload-an-image) dans notre guide d’utilisation

### Cache

* [Gestion du cache](/docs/commerce-admin/systems/tools/cache-management.html) dans le guide du système d’administration des utilisateurs.
* [Gérer le cache](/docs/commerce-operations/configuration-guide/cli/manage-cache.html) dans notre documentation destinée aux développeurs