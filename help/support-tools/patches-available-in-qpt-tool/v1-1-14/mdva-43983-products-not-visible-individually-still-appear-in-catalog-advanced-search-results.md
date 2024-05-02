---
title: '"MDVA-43983 : les produits définis comme "Non visibles individuellement" apparaissent dans les résultats de recherche"'
description: Le correctif MDVA-43983 résout le problème en raison duquel les produits définis comme "Non visibles individuellement" apparaissent toujours dans les résultats de recherche avancée du catalogue. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID de correctif est MDVA-43983. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 2599fb6c-5b27-461b-9740-f586ae7df9f5
feature: Catalog Management, Products, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-43983 : les produits définis comme &quot;Non visibles individuellement&quot; apparaissent dans les résultats de recherche.

Le correctif MDVA-43983 résout le problème en raison duquel les produits définis comme &quot;Non visibles individuellement&quot; apparaissent toujours dans les résultats de recherche avancée du catalogue. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.14 est installée. L’ID de correctif est MDVA-43983. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits définis comme &quot;Non visible individuellement&quot; apparaissent toujours dans les résultats de recherche avancée du catalogue.

<u>Étapes à reproduire</u>:

1. Création d’un attribut avec **Type d’entrée de catalogue pour le propriétaire du magasin** as **Liste déroulante** ou **Nuance visuelle** (par exemple, Couleur).
1. Définir **Utilisation dans la recherche** as **Oui** et **Visible dans la recherche avancée** as **Oui**.
1. Ajoutez certaines options d’attribut.
1. Création de produits avec **Visibilité** as **Non visible individuellement**.
1. Attribuer des options d’attribut de couleur.
1. Accédez au **Recherche avancée dans le catalogue** sur le storefront.
1. Sélectionnez uniquement l’option Attribut de couleur dans le champ Attribut de couleur et laissez le reste des champs vides ou tels quels.
1. Envoyez un formulaire de recherche avancée.
1. Observez les résultats de la recherche.

<u>Résultats attendus</u>:

Les produits définis comme &quot;Non visibles individuellement&quot; n’apparaissent pas dans les résultats de recherche avancée du catalogue.

<u>Résultats réels</u>:

Les produits définis comme &quot;Non visibles individuellement&quot; apparaissent dans les résultats de recherche avancée du catalogue.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
