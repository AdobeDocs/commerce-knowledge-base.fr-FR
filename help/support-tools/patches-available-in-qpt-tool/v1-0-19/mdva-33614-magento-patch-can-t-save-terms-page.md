---
title: "Correctif MDVA-33614 : impossible d’enregistrer la page Termes"
description: 'Le correctif MDVA-33614 corrige le problème lorsqu’il est impossible d’enregistrer les modifications apportées à la page Termes, car le Créateur de pages renvoie l’erreur suivante : *Une erreur s’est produite lors de l’initialisation du Créateur de pages. Veuillez consulter votre contact du support technique*. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 est installé. L’ID de correctif est MDVA-33614. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2."'
exl-id: d9b287bb-eab4-4c33-b725-ae0074962447
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Correctif MDVA-33614 : impossible d’enregistrer la page Termes

Le correctif MDVA-33614 corrige le problème lorsqu’il est impossible d’enregistrer les modifications apportées à la page Termes, car Page Builder renvoie l’erreur suivante : *Une erreur s’est produite lors du lancement du créateur de pages. Veuillez consulter votre contact d’assistance technique*. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.19 est installée. L’ID de correctif est MDVA-33614. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Il est impossible d’enregistrer les modifications apportées à la page Termes, car le Créateur de pages renvoie une erreur.

<u>Étapes à reproduire</u>:

1. Dans Commerce Admin, accédez à **CONTENU** > Eléments > **Pages**.
1. Sélectionnez la page Termes .
1. Cliquez sur **Modifier**.
1. Effectuez une modification et cliquez sur **Enregistrer**.

<u>Résultat attendu</u>:

La page est enregistrée sans erreur.

<u>Résultat réel</u>:

L&#39;erreur suivante s&#39;affiche : *Une erreur s’est produite lors du lancement du créateur de pages. Veuillez consulter votre contact d’assistance technique*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
