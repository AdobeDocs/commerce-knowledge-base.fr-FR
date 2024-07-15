---
title: Menu principal (Catégories) non affiché sur les sous-pages dont l’option est Fastly
description: Cet article fournit un correctif lorsque le menu principal (ou le [menu de navigation supérieure de catégorie](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) de notre guide d’utilisation) n’est pas affiché sur le storefront pour les sous-pages (par exemple, *blog/page*) lorsque l’option Fastly ou Varnish est activée.
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Menu principal (Catégories) non affiché sur les sous-pages dont l’option est Fastly

Cet article fournit un correctif pour les cas où le menu principal (ou le [menu de navigation supérieure de catégorie](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) dans notre guide d’utilisation) n’est pas affiché sur le storefront pour les sous-pages (par exemple, *blog/page*) lorsque l’option Fastly ou Varnish est activée.

**Cause :** le caractère non autorisé `/` (barre oblique) dans le paramètre *Clé URL* de la page (paramètres d’optimisation du moteur de recherche). Le caractère est généralement ajouté lorsque *Chemin d’accès à l’URL* (avec un emplacement de page entier) est spécifié par erreur au lieu de la *clé d’URL* : par exemple, *blog/page\_name* au lieu de simplement *page\_name*.

**Solution :** supprimez le caractère `/` (barre oblique) ; pour le paramètre *Clé URL*, indiquez uniquement le nom de la page.

## Versions affectées

* Adobe Commerce On-Premise 2.X.X
* Adobe Commerce sur l’infrastructure cloud 2.X.X
* Faciles ou vernis

## Problème

Le menu principal (également appelé le [menu de navigation supérieure de catégorie](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) dans notre guide d’utilisation) ne s’affiche pas sur le storefront pour les sous-pages lorsque l’option Fastly ou d’autres services de vernis sont activés.

## Cause

Le problème est dû au caractère non autorisé `/` (barre oblique), ajouté au paramètre *Clé URL* (Paramètres d’optimisation du moteur de recherche).

Le caractère est généralement ajouté lorsque *Chemin d’accès à l’URL* (avec tout l’emplacement de la page, y compris la ressource/le répertoire parent de la page) est spécifié par erreur au lieu de la *clé d’URL* : par exemple, *blog/page\_name* au lieu de simplement *page\_name*.

![Paramètre de clé URL pour les paramètres d’optimisation pour les moteurs de recherche](assets/seo_url_key.png)

## Solution

Supprimez le caractère `/` (barre oblique) du paramètre *URL Key* pour toutes les pages de votre magasin.

En d’autres termes, utilisez *URL Key* au lieu de *URL Path* : mentionnez simplement le nom de la page sans ressource/répertoire parent.

### Recommendations dans la hiérarchie des pages et l’optimisation pour les moteurs de recherche

Pour définir la hiérarchie des pages, utilisez la section **Hiérarchie** du menu Modifier la page.

![Paramètres de hiérarchie](assets/hierarchy_hr.png)

Vous pouvez également utiliser le menu **Contenu** > **Éléments** > **Hiérarchie** - pour des solutions de hiérarchie plus complexes.

À des fins d’optimisation pour les moteurs de recherche sur les pages de produits, utilisez les réécritures d’URL (**Marketing** > **Recherche et optimisation pour les moteurs de recherche** > **Réécritures d’URL**).

## Plus d’informations sur notre guide d’utilisation

Le paramètre *Clé URL* pour SEO :

* [Optimisation du moteur de recherche](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [Ajout d’une nouvelle page](/docs/commerce-admin/content-design/elements/pages/page-add.html)

Hiérarchie des pages :

* [Vue d’ensemble](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [Ajout d’un noeud](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
