---
title: '''MDVA-42269 : l’utilisateur administrateur ne peut pas se connecter à l’administrateur en raison de l’erreur "TypeError"'
description: Le correctif MDVA-42269 corrige le problème qui empêchait les utilisateurs administrateurs de se connecter à l’administrateur en raison de TypeError. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 est installé.  L’ID de correctif est MDVA-42269.  La dernière mise à jour de correctif est dans QPT 1.1.15. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 66d744a2-054e-493c-a060-9ed78447e35b
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-42269 : L’utilisateur administrateur ne peut pas se connecter à l’administrateur en raison de l’erreur &quot;TypeError&quot;

Le correctif MDVA-42269 corrige le problème qui empêchait les utilisateurs administrateurs de se connecter à l’administrateur en raison de TypeError. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 est installé.  L’ID de correctif est MDVA-42269.  La dernière mise à jour de correctif est dans QPT 1.1.15. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1, 2.3.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1 - 2.4.3-p2, 2.3.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs administrateurs ne peuvent pas se connecter à l’administrateur en raison de l’erreur suivante : *TypeError: strtotime() s’attend à ce que le paramètre 1 soit une chaîne, null étant donné.*

<u>Étapes à reproduire</u> :

Connectez-vous à l’administrateur Commerce.

<u>Résultats attendus</u> :

L’utilisateur administrateur peut se connecter à l’aide du nom d’utilisateur et du mot de passe appropriés.

<u>Résultats réels</u> :

L’utilisateur administrateur ne peut pas se connecter. L’erreur suivante est consignée : *TypeError: strtotime() exige que le paramètre 1 soit une chaîne, nul étant donné.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
