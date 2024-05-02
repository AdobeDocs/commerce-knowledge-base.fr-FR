---
title: 'MDVA-31343 patch : la mise à jour du planning supprime la classe body pour la catégorie'
description: Le correctif MDVA-31343 corrige le problème en raison duquel la classe CSS du corps de disposition affectée pour une catégorie est supprimée lors de la mise à jour planifiée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Le problème doit être corrigé dans Adobe Commerce 2.4.2.
exl-id: 50dbff01-cb77-4cac-b90e-5c4b06f5e4e7
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Correctif MDVA-31343 : la mise à jour du planning supprime la classe body pour la catégorie

Le correctif MDVA-31343 corrige le problème en raison duquel la classe CSS du corps de disposition affectée pour une catégorie est supprimée lors de la mise à jour planifiée. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.7 est installée. Le problème doit être corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La classe de corps de mise en page est supprimée de la catégorie après la mise à jour planifiée.

<u>Étapes à reproduire</u>:

1. Dans l’administrateur Commerce, créez une catégorie.
1. Définir **Disposition** = *Catégorie — Plein largeur* dans le **Conception** .
1. Enregistrez la catégorie.
1. Accédez à la page frontale de la catégorie. Dans la source de la page, notez que la variable

   ```css
   page-layout-category-full-width
   ```

   Classe CSS.
1. Sous **CATALOGUE** > **Catégorie**, cliquez sur **Planifier une nouvelle mise à jour** dans le *Modifications planifiées* pour la nouvelle catégorie.
1. Attendez que la mise à jour planifiée démarre, exécutez cron et videz le cache.
1. Accédez à la page de catégorie sur l’interface frontale et examinez la source de la page.

<u>Résultats attendus</u>:

Dans le corps de la page, le

```css
page-layout-category-full-width
```

Classe CSS.

<u>Résultats réels</u>:

Dans le corps de la page, le

```css
page-layout-2columns-left
```

Classe CSS, qui est par défaut pour la page de catégorie.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
