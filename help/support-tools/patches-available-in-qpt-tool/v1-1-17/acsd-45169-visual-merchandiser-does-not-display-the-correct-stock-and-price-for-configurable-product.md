---
title: "ACSD-45169 : le marchandisage visuel affiche un stock et un prix incorrects pour le produit configurable"
description: Le correctif ACSD-45169 corrige le problème en raison duquel le marchandiseur visuel n’affiche pas le stock et le prix corrects d’un produit configurable après l’application d’une mise à jour intermédiaire. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 est installé. L’ID de correctif est ACSD-45169. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: 5a7987c8-f276-4917-98f7-645402f4c454
feature: Categories, Configuration, Merchandising, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-45169 : le marchandisage visuel affiche un stock et un prix incorrects pour un produit configurable.

Le correctif ACSD-45169 corrige le problème en raison duquel le marchandiseur visuel n’affiche pas le stock et le prix corrects d’un produit configurable après l’application d’une mise à jour intermédiaire. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.17 est installée. L’ID de correctif est ACSD-45169. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 à 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le marchandisage visuel n’affiche pas le stock et le prix corrects d’un produit configurable après l’application d’une mise à jour intermédiaire.

<u>Étapes à reproduire</u>:

1. Créez un produit simple.
1. Créez une mise à jour planifiée pour le produit simple (vous devez simplement disposer de différents identifiants de ligne et d’entité).
1. Créez un produit configurable.
1. Attribuez le produit configurable à une catégorie.
1. Ouvrez la catégorie et observez le produit configurable dans la section Visual Merchandiser .

<u>Résultats attendus</u>:

Le marchandiseur visuel affiche le stock et le prix corrects.

<u>Résultats réels</u>:

Le marchandisage visuel affiche un stock et un prix incorrects.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
