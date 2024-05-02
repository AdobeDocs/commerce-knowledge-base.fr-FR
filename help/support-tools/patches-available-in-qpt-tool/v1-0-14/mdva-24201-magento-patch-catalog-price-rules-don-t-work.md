---
title: "MDVA-24201 : les règles de prix du catalogue ne fonctionnent pas"
description: Le correctif MDVA-24201 résout le problème en raison duquel les règles de prix du catalogue actives dans la base de données ne s’appliquent pas sur le front-end.
exl-id: ae541c40-403a-46e9-a486-2a1e8991f05a
feature: Catalog Management, Categories, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-24201 : Les règles de prix du catalogue ne fonctionnent pas

Le correctif MDVA-24201 résout le problème en raison duquel les règles de prix du catalogue actives dans la base de données ne s’appliquent pas sur le front-end.

Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.14 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.3.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.3

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Condition requise</u>:

Installez une nouvelle instance Magento avec des exemples de données.

<u>Étapes à reproduire</u>:

1. Connexion à **Panneau d’administration** > **Marketing** > **Règle de prix du catalogue** > **Ajouter une nouvelle règle**, définissez les paramètres suivants :
   1. Définissez la variable **Nom de la règle**.
   1. Définir **Actif** = *Non.*
   1. Définir des conditions : **Catégorie** = *4*. (Exemple : Bags)
   1. Définir des actions :
      1. Définir **Appliquer comme**   **pourcentage d’origine**.
      1. Définir **Montant de la remise** = *10*.
      1. Enregistrez, puis cliquez sur Continuer la modification.
   1. Cliquez sur **Planifier une nouvelle mise à jour**:
      * Définissez la variable **Nom de la règle**.
      * Définir **Actif** = *Oui*.
      * Enregistrez.
1. Accédez au serveur principal et exécutez :

   `php    bin/magento cron:run`

<u>Résultats attendus</u>:

Les prix des produits de la catégorie 4 &quot;Bags&quot; doivent être réduits de 10% du prix d&#39;origine, tel qu&#39;il a été défini par la règle de prix du catalogue, comme prévu.

<u>Résultats réels</u>:

Aucune modification de prix ne se produit même si la règle de prix du catalogue est active.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
