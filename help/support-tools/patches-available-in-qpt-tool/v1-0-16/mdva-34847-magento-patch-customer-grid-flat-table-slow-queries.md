---
title: "MDVA-34847 : customer_grid_plat table - requêtes lentes"
description: Le correctif MDVA-34847 résout le problème des requêtes lentes sur la table `customer_grid_plat`. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.
exl-id: e91cb86d-83cd-4267-a132-64465a57da7f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-34847 : requêtes lentes du tableau customer_grid_plat

Le correctif MDVA-34847 résout le problème des requêtes lentes sur la table `customer_grid_flat`. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.3

**Compatible avec les versions d’Adobe :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les requêtes lentes se produisent sur la table `customer_grid_flat`.

<u>Étapes à reproduire</u> :

1. Créez un utilisateur administrateur avec une portée personnalisée (par exemple : définissez **GWS** = *0,* et choisissez le site web par défaut existant avec **ID** = *1*).
1. Créez des produits et des éléments de catégorie.
1. Placez une commande à partir du front-end.
1. Connectez-vous à l’administrateur en tant que nouvel utilisateur.
1. Accédez à la grille Ventes (**Ventes > Commandes**).
1. Vérifiez que la requête SQL a été envoyée à DB (base de données).

<u>Résultats attendus</u> :

L’extension Admin GWS doit utiliser

```sql
int
```

des valeurs de

```sql
website_id
```

dans les conditions SQL, comme prévu :

```sql
main_table.website_id IN (1)
```

<u>Résultats réels</u> :

L’extension Admin GWS a ajouté une condition avec

```sql
website_id
```

value as

```sql
string
```

, par exemple :

```sql
main_table.website_id IN ('1')
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
