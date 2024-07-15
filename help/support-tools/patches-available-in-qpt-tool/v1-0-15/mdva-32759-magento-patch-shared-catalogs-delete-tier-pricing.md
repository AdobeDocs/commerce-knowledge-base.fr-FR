---
title: 'Correctif MDVA-32759 : catalogues partagés suppression du prix de niveau'
description: Le correctif MDVA-32759 résout le problème en raison duquel les catalogues partagés supprimaient la tarification de niveau existant.
exl-id: c6192d2f-cd25-483e-ba69-01ca62996faf
feature: B2B, Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Correctif MDVA-32759 : catalogues partagés suppression du niveau de prix

Le correctif MDVA-32759 résout le problème en raison duquel les catalogues partagés supprimaient la tarification de niveau existant.

Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Conditions préalables</u> :

Installez Adobe Commerce avec B2B, avec **Fonctionnalités B2B** activées.

<u>Étapes à reproduire</u> :

1. Accédez à **Magasins > Configuration > Fonctionnalités B2B > Activer l’entreprise** et **Catalogue partagé**.
1. Exécutez `bin/magento cron:run`.
1. Créez un produit simple, cliquez sur **Advanced PrTarification**, ajoutez **Catalog and Level price**, puis enregistrez-le.
1. Accédez à **Catalogue > Catalogue partagé > Définir la tarification et la structure**, cliquez sur **Configurer**, puis, dans ce menu déroulant, désélectionnez toutes les options et enregistrez.
1. Exécutez `bin/magento cron:run`.
1. Ouvrez le produit créé ci-dessus et vérifiez les tarifs avancés.

<u>Résultats attendus</u> :

Les prix de niveau ne doivent pas être supprimés des produits après la suppression de tous les produits du catalogue partagé public, comme prévu.

<u>Résultats réels</u> :

Les prix de niveau sont supprimés après la suppression de tous les produits du catalogue partagé public.


## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
