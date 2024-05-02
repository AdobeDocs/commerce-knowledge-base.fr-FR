---
title: "MDVA-39923 : la recherche par SKU dans la fonctionnalité d’ordre rapide B2B est sensible à la casse"
description: Le correctif MDVA-39923 corrige le problème en raison duquel les clients recevaient une erreur lorsqu’ils recherchaient la commande par SKU dans la fonctionnalité d’ordre rapide B2B avec une casse différente de celle avec laquelle le nom était enregistré. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-39923. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 52e435df-28a7-49be-a257-7e5801601d57
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-39923 : la recherche par SKU dans la fonctionnalité d’ordre rapide B2B est sensible à la casse.

Le correctif MDVA-39923 corrige le problème en raison duquel les clients recevaient une erreur lorsqu’ils recherchaient la commande par SKU dans la fonctionnalité d’ordre rapide B2B avec une casse différente de celle avec laquelle le nom était enregistré. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.2 est installée. L’ID de correctif est MDVA-39923. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La recherche par SKU dans la fonctionnalité d’ordre rapide B2B est sensible à la casse et affiche une erreur lorsqu’un autre cas est utilisé que celui avec lequel le SKU est enregistré.

<u>Conditions préalables</u>:

Les modules B2B sont installés.

<u>Étapes à reproduire</u>:

1. Connectez-vous à l’administrateur et accédez à **Magasins** > **Configuration** > **B2B**.
1. Activer **Catalogue partagé** et **Ordre rapide**.
1. Créez un produit avec un SKU majuscule, par exemple, TEST20-1234.
1. Attribuer le produit créé au **Catalogue partagé**.
1. Connectez-vous en tant que client et cliquez sur **Ordre rapide**.
1. Saisissez le SKU en minuscules, par exemple, test20-1234.

<u>Résultats attendus</u>:

Le produit doit être trouvé, quel que soit le cas utilisé.

<u>Résultats réels</u>:

Le message d’erreur suivant est reçu : *1 produit(s) auquel(s) vous devez prêter attention*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
