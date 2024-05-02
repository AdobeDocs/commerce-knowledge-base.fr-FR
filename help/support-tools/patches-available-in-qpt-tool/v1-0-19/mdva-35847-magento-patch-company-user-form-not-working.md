---
title: "MDVA-35847 : le formulaire utilisateur de l’entreprise ne fonctionne pas"
description: Le correctif MDVA-35847 résout le problème de non-fonctionnement du formulaire Utilisateur de la société et renvoie une erreur 500 sur le front-end. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 est installé. L’ID de correctif est MDVA-35847. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.
exl-id: 1a3f4a61-0c21-460a-ae48-e792d03ed805
feature: B2B, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-35847 : Le formulaire Utilisateur de l’entreprise ne fonctionne pas

Le correctif MDVA-35847 résout le problème de non-fonctionnement du formulaire Utilisateur de la société et renvoie une erreur 500 sur le front-end. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.19 est installée. L’ID de correctif est MDVA-35847. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Conditions préalables</u>:

Adobe Commerce B2B est installé.

<u>Étapes à reproduire</u>:

1. Accédez à **Magasins** > **Attributs** > **Client**, puis créez un attribut client personnalisé :

   * Type d’entrée = *Date*
   * Afficher sur Storefront = *Oui*
   * Ordre de tri = *0*
   * Forms à utiliser dans = *Tous les formulaires*

1. Créez une nouvelle société.
1. Connectez-vous en tant qu’administrateur de société sur le front-end.
1. Accédez aux sections Utilisateurs de l’entreprise .

<u>Résultats attendus</u>:

Le formulaire Utilisateur de l’entreprise se charge normalement.

<u>Résultats réels</u>:

Le formulaire Utilisateur de la société ne se charge pas et renvoie une erreur 500.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
