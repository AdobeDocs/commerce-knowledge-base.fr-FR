---
title: 'Correctif MDVA-33106 : les modifications de produit reprogrammées sont effacées après l’exécution de cron'
description: Le correctif MDVA-33106 corrige le problème en raison duquel les modifications de produit reprogrammées sont effacées après le cron.
exl-id: be32982c-796c-4069-ad70-37b5124ffb56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Correctif MDVA-33106 : les modifications de produit reprogrammées sont effacées après l’exécution de cron.

Le correctif MDVA-33106 corrige le problème en raison duquel les modifications de produit reprogrammées sont effacées après le cron.

```bash
bin/magento cron:run
```

est exécutée. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.13 est installée. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u>:

1. Dans Commerce Admin, accédez à **Catalogue** > **Produits** et cliquez sur modifier. Remarquez que la variable **Prix** par exemple *9,99*.
1. Cliquez sur **Planifier une nouvelle mise à jour** et renseignez les détails :
   * Le nom de la mise à jour n’est pas important.
   * Définissez une date dans le futur, +1 an pour les dates de début et de fin.
   * Définir le prix sur *1,99*.
   * Enregistrez les modifications.
1. Accédez au tableau de bord intermédiaire de contenu et sélectionnez le mode Grille pour voir si la correspondance planifiée ci-dessus est recherchée.
1. Sélectionnez l’action de modification en regard de la mise à jour planifiée. Les données doivent toujours correspondre à celles ci-dessus.
1. Remplacez la date planifiée par une date plus proche. À la place de +1 an à partir de maintenant, remplacez-le par + 1 semaine ou + 1 mois.
1. Enregistrez les modifications et vérifiez si les dates sont mises à jour dans le tableau de bord d’évaluation.
1. Attendez qu&#39;une tâche cron s&#39;exécute.
1. Cliquez à nouveau sur Modifier dans la modification planifiée et vérifiez le prix.

<u>Résultats attendus</u>:

Le prix est de 1,99.

<u>Résultats réels</u>:

Le prix est de 9,99.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
