---
title: 'MDVA-34886 : aucun résultat de recherche lorsque l’attribut "weight" est utilisé'
description: Le correctif MDVA-34886 résout le problème où la recherche renvoie des résultats lorsque l’attribut weight est configuré comme pouvant faire l’objet d’une recherche. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.
exl-id: e6f33772-0167-4a54-9d62-0ab89edb5d1d
feature: Attributes, Cache, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-34886 : aucun résultat de recherche lorsque l’attribut &quot;weight&quot; est utilisé

Le correctif MDVA-34886 résout le problème où la recherche renvoie des résultats lorsque l’attribut weight est configuré comme pouvant faire l’objet d’une recherche. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.2 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La recherche renvoie des résultats lorsque l’attribut weight est configuré comme pouvant faire l’objet d’une recherche.

<u>Étapes à reproduire</u> :

1. Configurez Elasticsearch.
1. Accédez à **Admin** > **Magasins** > **Attributs** > **Produit**. Modifiez l’attribut **Weight** et définissez son attribut **Searchable** = *Yes*.
1. Enregistrez l’attribut et effacez le cache de configuration.
1. Sur l’interface frontale, recherchez une valeur de texte (par exemple : *bag*).
1. Notez que la recherche ne renvoie aucun résultat.
1. Le journal des exceptions contient un message d’erreur du type :

```php
{"type":"number_format_exception","reason":"For input string: \"bag\""}
```

<u>Résultats attendus</u> :

La recherche renvoie des résultats même si l’attribut weight est configuré comme pouvant faire l’objet d’une recherche, comme prévu.

<u>Résultats réels</u> :

La recherche ne renvoie aucun résultat lorsque l’attribut weight est configuré comme pouvant faire l’objet d’une recherche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
