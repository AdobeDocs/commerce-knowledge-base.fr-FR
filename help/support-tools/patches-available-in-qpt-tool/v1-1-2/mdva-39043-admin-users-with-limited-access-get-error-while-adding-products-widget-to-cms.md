---
title: 'MDVA-39043 : les utilisateurs administrateurs reçoivent une erreur lors de l’ajout du widget à la page CMS'
description: Le correctif MDVA-39043 corrige le problème en raison duquel les utilisateurs administrateurs disposant d’un accès limité obtiennent une erreur lors de l’ajout du widget "Produits" à la page CMS. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 est installé. L’ID de correctif est MDVA-39043. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 63057351-e972-4575-9bf0-e818f590b40a
feature: Admin Workspace, CMS, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-39043 : les utilisateurs administrateurs reçoivent une erreur lors de l’ajout du widget à la page CMS.

Le correctif MDVA-39043 corrige le problème en raison duquel les utilisateurs administrateurs disposant d’un accès limité obtiennent une erreur lors de l’ajout du widget &quot;Produits&quot; à la page CMS. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.1.2 est installée. L’ID de correctif est MDVA-39043. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs administrateurs disposant d’un accès limité obtiennent une erreur lors de l’ajout du widget &quot;Produits&quot; à la page CMS.

<u>Étapes à reproduire</u>:

1. Connectez-vous au serveur principal à l’aide de l’administrateur avec accès uniquement pour modifier le contenu.
1. Accédez à **Contenu** > **Pages**.
1. Ouvrez une page à modifier.
1. Modifiez le contenu avec **Page Builder**.
1. Ajouter **Produit** widget depuis **Ajouter du contenu** .
1. Cliquez sur **Configurer** sur le **Produit** widget.

<u>Résultats attendus</u>:

Aucune erreur ne s’affiche.

<u>Résultats réels</u>:

Le message d’erreur suivant est reçu :

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
