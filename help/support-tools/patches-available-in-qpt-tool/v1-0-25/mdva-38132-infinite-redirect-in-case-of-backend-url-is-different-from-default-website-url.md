---
title: 'MDVA-38132 : redirection infinie lorsque l’URL du serveur principal est différente de l’URL du site web par défaut'
description: Le correctif MDVA-38132 corrige le problème de la redirection infinie lorsque l’URL du serveur principal est différente de l’URL du site web par défaut. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 est installé. L’ID de correctif est MDVA-38132. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: 122145d7-0961-47f8-8ab6-a15d62996e49
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38132 : Redirection infinie lorsque l’URL du serveur principal est différente de l’URL du site web par défaut

Le correctif MDVA-38132 corrige le problème de la redirection infinie lorsque l’URL du serveur principal est différente de l’URL du site web par défaut. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.25 est installée. L’ID de correctif est MDVA-38132. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
Adobe Commerce sur l’infrastructure cloud 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :**
Adobe Commerce (toutes les méthodes de déploiement) 2.3.3-2.4.2-p1
>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le panneau d’administration de Commerce comporte une redirection infinie lorsque l’URL du serveur principal est différente de l’URL du site web par défaut.

<u>Conditions préalables</u>:

* L’URL de base est utilisée pour le serveur principal et le storefront. L’URL sécurisée de base n’est pas utilisée.
* Le serveur web est configuré de sorte qu’Adobe Commerce soit accessible via deux URL différentes. URL1 est utilisée pour l’installation d’Adobe Commerce.

<u>Étapes à reproduire</u>:

1. Accédez au Panneau d’administration > **Magasins** > **Configuration** > **Web**.
1. Laissez l’URL de base d’origine dans la configuration globale. Il s’agit de votre URL 1.
1. Basculez vers la portée du site web principal.
1. Remplacez l’URL de base par une autre URL (voir les conditions préalables pour configurer correctement le serveur web). Il s’agit de votre URL 2.
1. Effacez le cache (si nécessaire et possible).
1. Ouvrez le panneau d’administration.

<u>Résultats attendus</u>:

Le panneau d’administration a été ouvert avec succès et vous pouvez y accéder. La boutique du site web principal a été ouverte et peut être consultée.

<u>Résultats réels</u>:

Une redirection infinie se produit. Adobe Commerce redirige de l’URL 1 vers l’URL 2 et continue d’aller et retour.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
