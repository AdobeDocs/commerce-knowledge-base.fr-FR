---
title: 'MDVA-28661 : problème avec la gestion des utilisateurs de l’entreprise lors du changement de l’email d’administration'
description: Le correctif MDVA-28861 corrige le problème d’erreur des utilisateurs lors de la modification de l’email de l’administrateur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 est installé. L’ID de correctif est MDVA-28861.
exl-id: 2d6691e5-baaf-4cef-ae7e-2b6ccc7f2cd3
feature: Admin Workspace, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28661 : problème avec la gestion des utilisateurs de l’entreprise lors du changement de l’email d’administration

Le correctif MDVA-28861 corrige le problème d’erreur des utilisateurs lors de la modification de l’email de l’administrateur. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.5 est installée. L’ID de correctif est MDVA-28861.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.0 à 2.4.1 (y compris 2.3.5-p1) avec extension B2B

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Après avoir modifié la variable **Administrateur de société** l’adresse électronique, une erreur est renvoyée et la variable **Utilisateurs de l’entreprise** ne s’affiche pas.

<u>Étapes à reproduire</u>:

1. Activation de la fonctionnalité d’entreprise (en savoir plus à ce sujet dans [Installation B2B : activation des fonctionnalités B2B dans l’administrateur Commerce](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin) dans notre documentation destinée aux développeurs et créez une société avec deux utilisateurs (un administrateur et deux utilisateurs), tous avec des adresses électroniques.
1. Accédez au **Administration de Commerce** > **Clients** > **Entreprises** et ouvrez votre compte de société.
1. Ouvrir **Administrateur de société** et remplacez admin par le premier utilisateur, ce qui inclut la modification de la variable **Administrateur de société** adresse électronique du premier utilisateur.
1. Accédez à l’interface utilisateur frontale d’Adobe Commerce et connectez-vous en tant que premier utilisateur.
1. Accédez au **Utilisateurs de l’entreprise** .

<u>Résultats attendus</u>:

La variable **Utilisateurs de l’entreprise** La liste doit s’afficher comme prévu.

<u>Résultats réels</u>:

La variable **Utilisateurs de l’entreprise** ne s’affiche pas, et une erreur similaire à celle-ci s’affiche :

```bash
No such entity with id = 2
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.

Pour en savoir plus sur la fonctionnalité d’entreprise B2B, reportez-vous à ces articles dans notre documentation destinée aux développeurs :

* [Guide du développeur B2B](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Gestion des rôles de l’entreprise](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Référence sur les chemins de configuration de l’extension Adobe Commerce Enterprise B2B](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
