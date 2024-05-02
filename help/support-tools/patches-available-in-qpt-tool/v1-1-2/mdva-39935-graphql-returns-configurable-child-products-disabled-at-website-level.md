---
title: "MDVA-39935 : GraphQL renvoie les produits enfants configurables désactivés au niveau du site web"
description: Le correctif Adobe Commerce MDVA-39935 corrige le problème en raison duquel GraphQL renvoie des produits enfants configurables désactivés au niveau du site web. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 est installé. L’ID de correctif est MDVA-39935. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 45bd6bd9-3572-4477-a689-d6b952a3290a
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39935 : GraphQL renvoie les produits enfants configurables désactivés au niveau du site web.

Le correctif Adobe Commerce MDVA-39935 corrige le problème en raison duquel GraphQL renvoie des produits enfants configurables désactivés au niveau du site web. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.1.2 est installée. L’ID de correctif est MDVA-39935. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

GraphQL renvoie les produits enfants configurables même après leur désactivation au niveau du site web.

<u>Étapes à reproduire</u>:

1. Activez l’option d’affichage des produits en rupture de stock sous **Magasin** > **Configuration** > **Catalogue** > **Inventaire** > **Options Stock** > **Afficher les produits en rupture de stock** > **Oui**.
1. Sélectionnez une **Produit configurable** qui comporte plus de deux **Produits simples**.
1. Désactiver **Produit simple** et enregistrez la variable **Produit configurable**.
1. Récupérer la variable **Produit configurable** à l’aide de GraphQL.

<pre>
  <code class="language-graphql">
{
  products(filter: { sku: { eq: "cp1" } }) {
    items {
      __typename
      name
      sku
      ... on ConfigurableProduct {
        variants {
          product {
            __typename
            name
            sku
            color
            stock_status
          }
        }
      }
    }
  }
}
</code>
</pre>

<u>Résultats attendus</u>:

Les produits désactivés ne s’affichent PAS dans les résultats des variantes.

<u>Résultats réels</u>:

Les données des produits désactivés sont récupérées dans les résultats des variantes.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
