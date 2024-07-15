---
title: "MDVA-40262 : les requêtes GraphQL ne s’affichent pas dans les termes de recherche les plus courants dans l’administration"
description: Le correctif de qualité MDVA-40262 Adobe Commerce corrige le problème en raison duquel les requêtes de recherche GraphQL ne s’affichent pas dans les termes de recherche courants dans l’administrateur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3 est installé. L’ID de correctif est MDVA-40262. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 7157e47d-a042-4462-96ed-23203a3213bd
feature: Admin Workspace, GraphQL, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-40262 : les requêtes GraphQL ne s’affichent pas dans les termes de recherche courants dans l’administration

Le correctif de qualité MDVA-40262 Adobe Commerce corrige le problème en raison duquel les requêtes de recherche GraphQL ne s’affichent pas dans les termes de recherche courants dans l’administrateur. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3 est installé. L’ID de correctif est MDVA-40262. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les requêtes GraphQL ne s’affichent pas dans les termes de recherche courants dans l’administrateur.

<u>Conditions préalables</u> :

Les exemples de données doivent être installés.

<u>Étapes à reproduire</u> :

1. Accédez à **Magasins** > **Configuration** > **Catalogue** > **SEO** > **Termes de recherche populaires** et définissez sur activer.
1. Exécutez la requête GraphQL suivante :

<pre>
<code class="language-graphql">
{
  products(
    search: "jackets"
    filter: { price: { to: "50" } }
    pageSize: 20
   ) {
    total_count
    items {
      name
      sku
    }
    page_info {
      page_size
      current_page
    }
  }
}
</code>
</pre>

<u>Résultats attendus</u> :

Après avoir exécuté la requête GraphQL pour rechercher un produit, la requête de recherche doit être ajoutée aux termes de recherche courants.

<u>Résultats réels</u> :

La requête de recherche n’est pas ajoutée aux termes de recherche courants.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* [Outil de correctifs de qualité publié : un nouvel outil pour appliquer des correctifs de qualité](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
