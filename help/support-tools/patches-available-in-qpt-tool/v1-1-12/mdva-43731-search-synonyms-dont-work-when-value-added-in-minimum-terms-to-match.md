---
title: '"MDVA-43731 : les synonymes de recherche ne fonctionnent pas lorsque la valeur est ajoutée dans "Termes minimum à faire correspondre""'
description: Le correctif MDVA-43731 corrige le problème en raison duquel les Synonymes de recherche ne fonctionnent plus lorsqu’une valeur est ajoutée dans "Termes minimum à faire correspondre". Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID de correctif est MDVA-43731. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: b795989c-d10b-443e-aebe-f3859930396a
feature: Cache, Marketing Tools, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-43731 : les synonymes de recherche ne fonctionnent pas lorsque la valeur est ajoutée dans &quot;Termes minimum à faire correspondre&quot;.

Le correctif MDVA-43731 corrige le problème en raison duquel les Synonymes de recherche ne fonctionnent plus lorsqu’une valeur est ajoutée dans &quot;Termes minimum à faire correspondre&quot;. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID de correctif est MDVA-43731. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les Synonymes de recherche cessent de fonctionner lorsqu’une valeur est ajoutée dans &quot;Termes minimum à faire correspondre&quot;.

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce avec des exemples de données.
1. Configurez Elasticsearch7 comme moteur de recherche.
1. Recherchez le mot &quot;Jacket&quot;. Une liste de produits s’affiche.
1. Ajoutez le paramètre [4&lt;60%] dans **Configuration** > **Catalogue** > **Recherche catalogue** > **Termes minimum à faire correspondre**.
1. Effacez le cache de configuration et effectuez une réindexation.
1. Recherchez à nouveau le mot &quot;Jacket&quot; et notez qu’une liste de produits s’affiche.
1. Accédez à **Marketing** > **SEO &amp; Search** > **Recherche de synonymes**.
1. Créez des synonymes de recherche en ajoutant les synonymes suivants : veste, bagtecs, express plus.
1. Effectuez une réindexation.
1. Effectuez une recherche de produit à l’aide de n’importe lequel des synonymes. Par exemple, veste.

<u>Résultats attendus</u> :

Vous obtenez la même liste de produits qu’auparavant dans les résultats de recherche.

<u>Résultats réels</u> :

Aucun produit n’est affiché dans les résultats de recherche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
