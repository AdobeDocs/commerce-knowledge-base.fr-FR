---
title: "MDVA-31307 : Mémoire insuffisante pour certaines catégories"
description: Le correctif MDVA-31307 corrige le problème où `Magento\_Csp/Model/BlockCache` consomme beaucoup de mémoire et génère d’énormes chaînes mises en cache, ce qui entraîne des problèmes pour certaines pages avec de nombreux scripts et styles de mise en whiteliste dynamique. Le correctif fourni optimise ce processus. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 est installé. L’ID de correctif est MDVA-31307. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307 : Mémoire insuffisante pour certaines catégories

Le correctif MDVA-31307 corrige le problème où `Magento\_Csp/Model/BlockCache` consomme beaucoup de mémoire et génère d’énormes chaînes mises en cache, ce qui entraîne des problèmes pour certaines pages avec de nombreux scripts et styles de mise en whiteliste dynamique. Le correctif fourni optimise ce processus. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.19 est installée. L’ID de correctif est MDVA-31307. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.4.0

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Correction du problème en raison duquel *Mémoire insuffisante* erreurs sur certaines catégories en raison de problèmes de mise en whiteliste dynamique CSP pour les blocs mis en cache.

<u>Étapes à reproduire :</u>

1. Générer des fixations de profil de petite taille (`bin/magento setup:performance:generate-fixtures`).
1. Ouvrez toutes les pages de catégorie dans différents onglets.

<u>Résultat réel :</u>

*[date et heure] Erreur fatale PHP : taille de mémoire autorisée de 1073741824 octets épuisée (tentative d’allocation de 9 012 octets) dans Inconnu sur la ligne 0
[date et heure] Erreur fatale PHP : taille de mémoire autorisée de 1073741824 octets épuisée (tentative d’allocation de 33554440 octets) dans /app/`<project-id>`/vendor/magento/module-csp/Model/Collector/DynamicCollector.php en ligne 31*

<u>Résultat attendu :</u>

Toutes les pages se sont ouvertes correctement.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
