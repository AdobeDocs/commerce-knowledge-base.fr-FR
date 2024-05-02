---
title: '"MDVA-42341 : la requête GraphQL "categoryList" ne filtre pas les résultats"'
description: Le correctif MDVA-42341 résout le problème en raison duquel la requête GraphQL "categoryList" ne filtre pas les résultats si une requête comporte l’en-tête Magasin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 est installé. L’ID de correctif est MDVA-42341. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 34aeb30a-9491-4102-b33e-dcd857b6a1c2
feature: GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42341 : la requête GraphQL &quot;categoryList&quot; ne filtre pas les résultats

Le correctif MDVA-42341 résout le problème en raison duquel la requête GraphQL &quot;categoryList&quot; ne filtre pas les résultats si une requête comporte l’en-tête Magasin. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.8 est installée. L’ID de correctif est MDVA-42341. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête GraphQL &quot;categoryList&quot; ne filtre pas les résultats si une requête comporte l’en-tête Magasin .

<u>Étapes à reproduire</u>:

1. Création d’une catégorie racine et attribution d’un nom à cette catégorie **root2**.
1. Créez un second site web/magasin/storeview et affectez-lui **root2** dans le nouveau magasin.
1. Créez une nouvelle catégorie sous Catégorie racine par défaut = catégorie1.
1. À l’aide d’une requête GraphQL, obtenez une liste de catégories pour le deuxième site web (utilisez Header store = new).

<pre>
<code class="language-graphql">
{
  categoryList(filters: {name: {match: "category1"}}) {
    uid
    level
    name
    breadcrumbs {
      category_uid
      category_name
      category_level
      category_url_key
    }
  }
}
</code>
</pre>

<u>Résultats attendus</u>:

Les catégories de la catégorie racine par défaut ne sont pas répertoriées en réponse, car nous utilisons un &quot;nouvel&quot; en-tête de magasin.

<u>Résultats réels</u>:

Les catégories de la catégorie racine par défaut sont disponibles dans les résultats.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
