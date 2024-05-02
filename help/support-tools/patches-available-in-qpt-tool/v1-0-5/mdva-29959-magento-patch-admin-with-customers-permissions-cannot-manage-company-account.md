---
title: 'Correctif "MDVA-29959 : l’administrateur avec les autorisations "Les clients" ne peut pas gérer le compte de l’entreprise"'
description: Le correctif MDVA-29959 disponible dans l’outil [Outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) version 1.0.5 corrige le problème lorsqu’un utilisateur administrateur restreint disposant de toutes les autorisations pour l’ACL "client" ne peut pas gérer les entreprises (ajouter ou supprimer une entreprise). Veuillez noter que le problème a été corrigé dans B2B pour Adobe Commerce 2.3.4.
exl-id: ee246380-d37e-4c24-8435-97ae80088227
feature: Admin Workspace, B2B, Companies, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Correctif MDVA-29959 : l’administrateur avec les autorisations &quot;Clients&quot; ne peut pas gérer le compte de l’entreprise

Correctif MDVA-29959 disponible dans le [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.5 de l’outil corrige le problème lorsqu’un utilisateur administrateur restreint avec toutes les autorisations pour la liste de contrôle d’accès &quot;client&quot; ne peut pas gérer les entreprises (ajouter ou supprimer une société). Veuillez noter que le problème a été corrigé dans B2B pour Adobe Commerce 2.3.4.

## Produits et versions concernés

B2B pour Adobe Commerce sur l’infrastructure cloud 2.3.0-2.3.3-p1.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un utilisateur administrateur disposant de toutes les autorisations pour la liste de contrôle d’accès &quot;client&quot; ne peut pas gérer les entreprises (ajouter ou supprimer une société).

<u>Étapes à reproduire</u>

1. Dans l’administrateur Commerce, créez un rôle d’administrateur et affectez un utilisateur à ce rôle.
1. Affectez uniquement des ressources &quot;Client&quot; au rôle.
1. Connectez-vous en tant qu’utilisateur avec ce rôle.
1. Essayez de supprimer un compte de société.

<u>Résultat attendu :</u>

Le compte de la société a été supprimé.

<u>Résultat réel :</u>

Vous ne pouvez pas supprimer le compte de la société. Vous obtenez le *Vous avez besoin d&#39;autorisations pour afficher ce contenu.* message d’erreur.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
