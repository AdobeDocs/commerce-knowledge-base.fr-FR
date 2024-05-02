---
title: "MDVA-37592 : Le tri par prix ne fonctionne pas pour les produits dont le prix est nul"
description: Le correctif Adobe Commerce MDVA-37592 résout le problème en raison duquel le tri par prix ne fonctionne pas correctement pour les produits dont le prix est nul affecté à un catalogue partagé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 est installé. L’ID de correctif est MDVA-37592. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 30ac1e87-c32d-4e79-9ed9-d1861061d760
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-37592 : Le tri par prix ne fonctionne pas pour les produits dont le prix est nul

Le correctif Adobe Commerce MDVA-37592 résout le problème en raison duquel le tri par prix ne fonctionne pas correctement pour les produits dont le prix est nul affecté à un catalogue partagé. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.0 est installée. L’ID de correctif est MDVA-37592. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur notre architecture cloud 2.4.0-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (tous les types de déploiement) 2.3.6-2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le tri par prix ne fonctionne pas correctement pour les produits dont le prix est nul affecté à un catalogue partagé.

<u>Conditions préalables</u>:

B2B est installé.

<u>Étapes à reproduire</u>:

1. Activez le catalogue partagé.
1. Créez quatre produits avec les prix suivants et attribuez-les à une catégorie : 50, 60, 70 et 80 USD.
1. Créez un catalogue partagé avec les produits ci-dessus.
1. Définissez le prix personnalisé sur zéro pour le produit dont le prix est de 70 $.
1. Créez maintenant un utilisateur de l’entreprise et affectez-le au catalogue partagé qui vient d’être créé.
1. Connectez-vous à l’aide du compte de l’entreprise et accédez à la catégorie à laquelle les produits sont affectés.
1. Essayez de trier par prix.

<u>Résultats attendus</u>:

Le produit dont le prix est nul est correctement trié.

<u>Résultats réels</u>:

Le produit dont le prix est zéro n’est PAS correctement trié. À la place, il est trié en fonction du prix d’origine.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce on-premise : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur notre architecture cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
