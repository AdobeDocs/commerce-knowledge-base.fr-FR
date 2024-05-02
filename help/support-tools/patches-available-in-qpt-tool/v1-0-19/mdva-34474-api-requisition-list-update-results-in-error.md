---
title: 'MDVA-34474 : la mise à jour de la liste des demandes d’API entraîne une erreur'
description: Le correctif MDVA-34474 corrige le problème en raison duquel l’ajout d’un produit à la liste de demandes à l’aide de l’API générait une erreur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 est installé. L’ID de correctif est MDVA-34474. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: dc39c4f7-417c-45ea-914c-32f7305527da
feature: REST, B2B
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-34474 : la mise à jour de la liste des demandes d’API entraîne une erreur

Le correctif MDVA-34474 corrige le problème en raison duquel l’ajout d’un produit à la liste de demandes à l’aide de l’API générait une erreur. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.19 est installée. L’ID de correctif est MDVA-34474. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.0

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.0 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’ajout d’un produit à la liste des demandes d’acquisition à l’aide de l’API entraîne une erreur.

<u>Étapes à reproduire</u>:

1. Activer la liste des demandes d’acquisition dans Admin (**Magasins** > **Configuration** > **Général** > **Fonctionnalités B2B** > **Activer la liste de demandes** = *Oui*).
1. Créez un client.
1. Création d’une liste de demandes pour cet appel d’envoi de client ```json    POST rest/all/V1/requisition_lists``` avec la charge utile json associée.

<u>Résultats attendus</u>:

Aucune erreur et la liste est créée.

<u>Résultats réels</u>:

Erreur 400.

```json
{"message":"Could not save Requisition List"}
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
