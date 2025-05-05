---
title: '''MDVA-38447: "Non visible individuellement" les produits enfants configurables sont renvoyés dans la réponse GraphQL et la requête MySQL lente"'
description: Le correctif Adobe Commerce MDVA-38447 corrige le problème en raison duquel les produits enfants configurables "Non visibles individuellement" sont renvoyés dans la réponse GraphQL et la requête MySQL lente pour les produits GraphQL avec filtre de catégorie. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-38447. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 302e7458-d9ea-466a-a2ac-d86a8ee3eca3
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-38447 : les produits enfants configurables &quot;non visibles individuellement&quot; sont renvoyés dans la réponse GraphQL et la requête MySQL lente.

Le correctif Adobe Commerce MDVA-38447 corrige le problème en raison duquel les produits enfants configurables &quot;Non visibles individuellement&quot; sont renvoyés dans la réponse GraphQL et la requête MySQL lente pour les produits GraphQL avec filtre de catégorie. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-38447. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits enfants configurables &quot;non visibles individuellement&quot; sont renvoyés dans la réponse GraphQL et la requête MySQL lente pour les produits GraphQL avec filtre de catégorie.

<u>Conditions préalables</u> :

Les modules B2B doivent être installés.

<u>Étapes à reproduire</u> :

1. Créez un produit configurable avec des produits simples définis sur **Non visible individuellement**.
1. Exécutez une **réindexation complète**.
1. Exécutez une **requête GraphQL** comme :

<pre>query getFilteredProducts(
  $filter : ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search: String
  $pageSize: Int!
  $currentPage : Int!
) &lbrace;
  products(
    filter : $filter
    sort : $sort
    search: $search
    pageSize : $pageSize
    currentPage : $currentPage
  ) &lbrace;
    total_count
    page_info &lbrace;
      total_pages
      current_page
      page_size
    &rbrace;
    items &lbrace;
      name
      sku
    &rbrace;
  &rbrace;
&rbrace;</pre>

Variables :

<pre>&lbrace;"filter":{"user_group":{"eq":""},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Résultats attendus</u> :

Les produits dont la visibilité est définie sur &quot;Non visible individuellement&quot; ne seront pas renvoyés en réponse.

<u>Résultats réels</u> :

Les produits dont la visibilité est définie sur &quot;Non visible individuellement&quot; sont renvoyés en réponse.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* [Outil de correctifs de qualité publié : un nouvel outil pour appliquer des correctifs de qualité](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
