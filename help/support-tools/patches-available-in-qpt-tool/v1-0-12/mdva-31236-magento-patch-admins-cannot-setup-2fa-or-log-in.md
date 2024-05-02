---
title: 'MDVA-31236 : les administrateurs ne peuvent pas configurer 2FA ou se connecter'
description: Le correctif MDVA-31236 corrige le problème en raison duquel les utilisateurs administrateurs de Commerce ayant un accès aux ressources personnalisées ne peuvent pas configurer [authentification à deux facteurs (2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html) ni se connecter. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 est installé.
exl-id: b75d7a19-3c17-4389-b359-7aeeb8797539
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# MDVA-31236 : les administrateurs ne peuvent pas configurer 2FA ni se connecter.

Le correctif MDVA-31236 corrige le problème où les utilisateurs administrateurs de Commerce ayant un accès aux ressources personnalisées ne peuvent pas configurer [authentification à deux facteurs (2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html) ou vous connecter. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.12 est installée.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.4.0.

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.4.0-2.4.1.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne disposant pas de privilèges d’administrateur ne peuvent actuellement pas configurer leur accès 2FA personnel. 2FA tel qu’il est implémenté dans Adobe Commerce comprend deux rôles ACL. Un rôle a une incidence sur la configuration globale du système et il n’est nécessaire que lors de la configuration du système. Le deuxième rôle de liste de contrôle d’accès affecte des comptes utilisateur individuels 2FA. Un utilisateur administrateur doit configurer ce deuxième type de liste de contrôle d’accès 2FA.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
