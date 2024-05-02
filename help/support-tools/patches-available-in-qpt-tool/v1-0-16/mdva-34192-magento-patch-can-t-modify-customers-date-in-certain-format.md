---
title: "Correctif MDVA-34192 : impossible de modifier la date des clients dans un certain format"
description: Le correctif MDVA-34192 corrige le problème lorsqu’il est impossible de modifier/spécifier la date de naissance du client au format jj/mm/aaaa. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: 8aa36970-b2bf-43f8-ba8f-bfc144f8d4ab
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Correctif MDVA-34192 : impossible de modifier la date des clients dans un certain format

Le correctif MDVA-34192 corrige le problème lorsqu’il est impossible de modifier/spécifier la date de naissance du client au format jj/mm/aaaa. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.16 est installée. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :** 2.3.4-2.3.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le correctif résout plusieurs problèmes. Vous trouverez ci-dessous la description et les étapes à reproduire pour l’un d’eux.

Le filtre de grille de produit ne fonctionne pas correctement lorsque nous le filtrons à l’aide d’un attribut de date personnalisé et que le paramètre régional de l’utilisateur administrateur est en\_GB.

<u>Étapes à reproduire :</u>:

1. Créez un utilisateur administrateur dont **Paramètres régionaux de l’interface** est défini sur *Anglais (Royaume-Uni)*.
1. Créez un attribut de date avec la configuration suivante :
   * **Type d’entrée de catalogue pour le propriétaire du magasin**: *Date*
   * **Utilisation dans les options de filtre**: *Oui*
   * **Ajouter aux options de colonne**: *Oui*
1. Attribuez l’attribut à un jeu d’attributs.
1. Accédez à la page de modification du produit, sélectionnez une date pour le nouvel attribut à l’aide du sélecteur de date et enregistrez.
1. Essayez de filtrer la grille de produit à l’aide du nouvel attribut de date.

<u>Résultat attendu :</u>:

Le filtre de produit fonctionne correctement pour un attribut de date personnalisé lorsque le paramètre régional de l’utilisateur admin est en\_GB.

<u>Résultat réel :</u>:

Le filtre de produit ne fonctionne pas correctement pour un attribut de date personnalisé lorsque le paramètre régional de l’utilisateur admin est en\_GB.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants, en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
