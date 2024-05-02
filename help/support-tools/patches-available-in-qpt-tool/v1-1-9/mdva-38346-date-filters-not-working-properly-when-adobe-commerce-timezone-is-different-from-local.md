---
title: 'MDVA-38346 : les filtres de date ne fonctionnent pas lorsque le fuseau horaire Adobe Commerce est différent de local'
description: Le correctif MDVA-38346 résout le problème en raison duquel les filtres de dates ne fonctionnent pas correctement lorsque le fuseau horaire Adobe Commerce est différent du fuseau horaire de l’environnement local. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 est installé. L’ID de correctif est MDVA-38346. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 221ac249-add3-46e9-b0da-688eacdb753e
feature: Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-38346 : les filtres de date ne fonctionnent pas lorsque le fuseau horaire Adobe Commerce est différent de local

Le correctif MDVA-38346 résout le problème en raison duquel les filtres de dates ne fonctionnent pas correctement lorsque le fuseau horaire Adobe Commerce est différent du fuseau horaire de l’environnement local. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.9 est installée. L’ID de correctif est MDVA-38346. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1, 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les filtres de dates ne fonctionnent pas correctement lorsque le fuseau horaire Adobe Commerce est différent du fuseau horaire de l’environnement local.

<u>Étapes à reproduire</u>:

1. Définissez le fuseau horaire sur Australia/Sydney.
1. Prenez peu de commandes.
1. Créez des factures pour eux.
1. Accédez à **Ventes** > **Facturations** et filtrer par Date de facture (date courante - date courante).
1. Vérifier les dates.

<u>Résultats attendus</u>:

La date de facture affichée et la correspondance réelle du filtre.

<u>Résultats réels</u>:

La date de facture affichée est en avance d&#39;un jour sur le filtre réel (date courante + 1 jour).

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
