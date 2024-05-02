---
title: 'MDVA-38468 : Recevez un message d’erreur lors de l’enregistrement de la page CMS'
description: '''Le correctif Adobe Commerce MDVA-38468 corrige le problème où les utilisateurs reçoivent le message d’erreur : *L’élément avec le même ID "PAGE_ID" existe déjà* lors de l’enregistrement d’une page CMS. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26 est installé. L’ID de correctif est MDVA-38468. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.6."'
exl-id: 7fe80308-50b7-4786-a43c-cce607eb606c
feature: CMS, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-38468 : Recevez un message d’erreur lors de l’enregistrement de la page CMS

Le correctif Adobe Commerce MDVA-38468 corrige le problème où les utilisateurs reçoivent le message d’erreur : *Un élément avec le même ID &quot;PAGE_ID&quot; existe déjà,* lors de l’enregistrement d’une page CMS. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.26 est installée. L’ID de correctif est MDVA-38468. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
Adobe Commerce sur l’infrastructure cloud 2.3.2-p2

**Compatible avec les versions d’Adobe Commerce :**
Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.2-2.3.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque vous essayez d’enregistrer une page CMS, vous recevez le message d’erreur suivant : *Un élément avec le même ID &quot;PAGE_ID&quot; existe déjà.*

<u>Étapes à reproduire</u>:

1. Créez un site Web + Magasin + Aperçu du magasin.
1. Créez un site Web supplémentaire + Magasin + Aperçu du magasin.
1. Accédez à **Contenu** > **Hiérarchie** > Ajoutez toute page CMS existante à l’arborescence de hiérarchie.
1. Accédez à **Contenu** > **Pages** > **Ajouter une nouvelle page**:
   * Ajoutez n’importe quel titre.
   * Dans Page de la section Sites web , affectez-lui les deux vues de magasin créées.
   * Dans la section Hiérarchie , affectez-vous à n’importe quelle catégorie.
   * **Enregistrer et continuer la modification**.

<u>Résultats attendus</u>:

La page est enregistrée sans erreur.

<u>Résultats réels</u>:

La page est enregistrée, mais le message d’erreur suivant s’affiche : *Un élément (Magento\VersionsCms\Model\Hierarchy\Node) avec le même ID &quot;PAGE_ID&quot; existe déjà.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
