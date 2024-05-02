---
title: 'MDVA-37984 : le marchandisage visuel ne fonctionne pas correctement lors de l’application de mises à jour intermédiaires'
description: Le correctif MDVA-37984 résout le problème en raison duquel la fonctionnalité "Faire correspondre le produit par règle" du marchandiseur visuel ne filtre pas correctement les produits lors de l’application de mises à jour intermédiaires. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 est installé. L’ID de correctif est MDVA-37984. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: d806b94c-3b22-4d4c-8afb-7b57a0ebfe46
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-37984 : le marchandisage visuel ne fonctionne pas correctement lors de l’application de mises à jour intermédiaires.

Le correctif MDVA-37984 résout le problème en raison duquel la fonctionnalité &quot;Faire correspondre le produit par règle&quot; du marchandiseur visuel ne filtre pas correctement les produits lors de l’application de mises à jour intermédiaires. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.9 est installée. L’ID de correctif est MDVA-37984. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La fonctionnalité &quot;Match product by rule&quot; du marchandiseur visuel ne filtre pas correctement les produits lorsque des mises à jour intermédiaires sont appliquées.

<u>Étapes à reproduire</u>:

1. Créez une mise à jour de planification pour tout produit existant.
   * Définir différentes valeurs pour `entity_id` et `row_id`.
1. Créez un produit configurable, puis un produit simple (le nouveau produit, par conséquent). `entity_id` et `row_ids` sont également différents).
   * Pour faciliter la réplication du problème, définissez une valeur de quantité reconnaissable pour le produit simple, par exemple 5000.
1. Positionnez-vous dans une catégorie > **Produits dans la catégorie** et activez **Correspondance de produits par règle**.
1. Sélectionnez maintenant &quot;Quantité&quot; comme attribut, &quot;Supérieur&quot; comme opérateur et &quot;4500&quot; comme valeur.
1. Cliquez sur **save**.

<u>Résultats attendus</u>:

Le produit configurable nouvellement créé est répertorié.

<u>Résultats réels</u>:

Le produit configurable nouvellement créé n’est pas répertorié.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
