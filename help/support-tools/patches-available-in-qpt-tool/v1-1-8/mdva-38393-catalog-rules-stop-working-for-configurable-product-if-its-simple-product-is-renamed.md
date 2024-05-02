---
title: 'MDVA-38393 : les règles du catalogue cessent de fonctionner pour un produit configurable si son produit simple est renommé'
description: Le correctif MDVA-38393 corrige le problème en raison duquel les règles du catalogue ne fonctionnent plus pour un produit configurable si son produit simple est renommé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 est installé. L’ID de correctif est MDVA-38393. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: a20856c4-8aff-427b-a404-7afe706be06f
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38393 : les règles du catalogue cessent de fonctionner pour un produit configurable si son produit simple est renommé

Le correctif MDVA-38393 corrige le problème en raison duquel les règles du catalogue ne fonctionnent plus pour un produit configurable si son produit simple est renommé. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.8 est installée. L’ID de correctif est MDVA-38393. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les règles du catalogue cessent de fonctionner pour un produit configurable si son produit simple est renommé.

<u>Étapes à reproduire</u>:

1. Créez un produit configurable avec un produit simple associé.
1. Créez une catégorie.
1. Attribuez uniquement le produit configurable à la nouvelle catégorie.
1. Créer de nouvelles règles de catalogue :
   * Condition = La catégorie contient \&lt;new category=&quot;&quot; id=&quot;&quot;>
   * Action = réduction de 50 %
   * Actif = Oui
1. Effectuez la réindexation.
1. Vérifiez le produit paramétrable sur le front-end (la réduction doit être appliquée).
1. Vérifiez les `catalogrule_product` table (le produit simple doit bénéficier d’une remise).
1. Accédez à l’administrateur et modifiez le nom du produit simple. Cela ajoute un enregistrement à la variable `catalogrule_product_cl` table.
1. Exécutez le cron ou le `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` .
1. Vérifiez les `catalogrule_product` table.

<u>Résultats attendus</u>:

Le produit configurable offre une remise.

<u>Résultats réels</u>:

* Les enregistrements de réduction créés pour les produits simples sont manquants dans la variable `catalogrule_product` table.
* Le produit configurable sur l’interface a le prix d’origine complet.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
