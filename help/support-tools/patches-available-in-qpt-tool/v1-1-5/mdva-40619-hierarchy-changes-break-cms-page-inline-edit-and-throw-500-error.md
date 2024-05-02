---
title: 'MDVA-40619 : les modifications de hiérarchie interrompent l’édition en ligne de la page CMS et génèrent une erreur 500'
description: Le correctif MDVA-40619 résout le problème en raison duquel les modifications de la hiérarchie de la page CMS interrompent la modification en ligne de la page CMS et génèrent "500 erreurs". Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 est installé. L’ID de correctif est MDVA-40619. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: c003d845-1ba0-49c0-9f1a-a4b0ec00f30c
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40619 : les modifications de hiérarchie interrompent l’édition en ligne de la page CMS et génèrent une erreur 500

Le correctif MDVA-40619 résout le problème en raison duquel les modifications de la hiérarchie de la page CMS interrompent la modification en ligne de la page CMS et génèrent &quot;500 erreurs&quot;. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.5 est installée. L’ID de correctif est MDVA-40619. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les modifications de la hiérarchie de la page CMS rompent la modification en ligne de la page CMS et génèrent &quot;une erreur 500&quot;.

<u>Étapes à reproduire</u>:

1. Accédez au Panneau d’administration > **Contenu** > **Hiérarchie**.
1. Sélectionnez &quot;Affichage de magasin par défaut&quot;.
1. Décochez la case &quot;Utiliser la hiérarchie des noeuds parents&quot;.
1. Sélectionnez la page manuellement, puis cliquez sur **Enregistrer**.
1. Ensuite, sélectionnez **Contenu** > **Pages**.
1. Essayez de modifier une page CMS de la grille.
1. Cliquez sur **Enregistrer**.

<u>Résultats attendus</u>:

La page est enregistrée avec succès.

<u>Résultats réels</u>:

Vous obtenez l’erreur suivante :

*Un problème technique avec le serveur a créé une erreur. Essaie de nouveau de continuer ce que tu étais en train de faire. Si le problème persiste, réessayez plus tard.*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
