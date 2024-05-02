---
title: 'MDVA-29042 : autorisations de catégorie globale inchangées'
description: Le correctif MDVA-29042 corrige le problème en raison duquel les autorisations du catalogue étaient remplacées automatiquement par "*Autoriser*" après l’ajout d’un nouveau produit au catalogue partagé dans l’administrateur Commerce. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.6 avec l’extension B2B.
exl-id: 491b8881-87ec-4820-8f87-54961682e961
feature: Catalog Management, Categories, Customer Service, Roles/Permissions
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29042 : autorisations de catégorie globale inchangées

Le correctif MDVA-29042 corrige le problème en raison duquel les autorisations du catalogue étaient remplacées par &quot;*Autoriser*&quot; automatiquement après l’ajout d’un nouveau produit au catalogue partagé dans l’administrateur Commerce. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.5 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.6 avec l’extension B2B.

## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) 2.3.3 à 2.3.4-p2 avec extension B2B

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La désélection d’un groupe de clients des autorisations de catégorie globale dans l’administrateur Commerce ne définit pas automatiquement ce groupe de clients sur &quot;*Refuser*&quot; dans les autorisations de catégorie.

<u>Conditions préalables</u>:

* Instance B2B avec un groupe de clients défini et sélectionné sous **MAGASINS** > **Configuration** > **CATALOGUE** > **Catalogue** > **Autorisations de catégorie** pour :
   * **Autoriser la catégorie de navigation**
   * **Afficher les prix des produits**
   * **Autoriser l’ajout au panier**
* Sous chaque **Catégorie**, le groupe de clients est défini comme &quot;&quot;*Autoriser*&quot; pour :
   * **Catégorie de navigation**
   * **Afficher les prix des produits**
   * **Ajouter au panier**

<u>Étapes à reproduire</u>:

1. Dans l’administrateur de Commerce, accédez à **MAGASINS** > **Configuration** > **CATALOGUE** > **Catalogue** > **Autorisations de catégorie** et désélectionnez le groupe de clients dans :
   * **Autoriser la catégorie de navigation**
   * **Afficher les prix des produits**
   * **Autoriser l’ajout au panier**
1. Cliquez sur le bouton **Enregistrer la configuration** bouton .
1. Attendez que les indexeurs s’exécutent.
1. Regarder **CATALOGUE** > **Catégories** > **Autorisations de catégorie**.

<u>Résultats attendus</u>:

**Autorisations de catégorie** sera défini sur &quot;*Refuser*&quot; pour toutes les catégories du groupe de clients.

<u>Résultats réels</u>:

Aucune modification n’est apportée aux autorisations de catégorie pour le groupe de clients.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.

Pour en savoir plus sur les fonctionnalités de l’entreprise B2B, reportez-vous aux articles suivants dans notre documentation destinée aux développeurs :

* [Guide du développeur B2B](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Gestion des rôles de l’entreprise](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Référence sur les chemins de configuration de l’extension Adobe Commerce Enterprise B2B](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
