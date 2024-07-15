---
title: '''Correctif MDVA-27664 : date d''erreur du compte de naissance'''
description: Le correctif MDVA-27664 résout le problème en raison duquel la date de naissance d’un compte client peut être supérieure à aujourd’hui.
exl-id: c669764e-b4a5-4031-92ac-1156755e9a0a
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Correctif MDVA-27664 : date d&#39;erreur du compte de naissance

Le correctif MDVA-27664 résout le problème en raison duquel la date de naissance d’un compte client peut être supérieure à aujourd’hui.

Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.3.6.

## Produits et versions concernés

**Le correctif est créé pour la version d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur.
1. Définissez **Locale** = *en\_GB* (Royaume-Uni) pour un utilisateur.
1. Modifier un client.
1. Sélectionnez une date de naissance après le 12 d&#39;un mois de cette année.

<u>Résultats attendus</u> :

La date de naissance est valide, de sorte que les informations du client peuvent être enregistrées, comme prévu.

<u>Résultats réels</u> :

Les informations sur les clients ne peuvent pas être enregistrées car une erreur de validation se produit :

```php
The Date of Birth should not be greater than today.
```

où au lieu du format de date JJ/MM/AAAA, la date est traitée comme le format de date MM/JJ/AAAA.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
