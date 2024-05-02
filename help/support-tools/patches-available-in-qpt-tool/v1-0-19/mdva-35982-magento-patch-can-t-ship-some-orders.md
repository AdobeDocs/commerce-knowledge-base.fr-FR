---
title: "MDVA-35982 : impossible d’envoyer certaines commandes"
description: Le correctif MDVA-35982 corrige l’erreur lorsque l’utilisateur administrateur limité à un site web spécifique ne peut pas créer d’envoi pour la commande passée sur le même site web. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 est installé. L’ID de correctif est MDVA-35982. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: f41c6572-66bb-4697-93e3-da34b81829e2
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-35982 : impossible d’envoyer certaines commandes

Le correctif MDVA-35982 corrige l’erreur lorsque l’utilisateur administrateur limité à un site web spécifique ne peut pas créer d’envoi pour la commande passée sur le même site web. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.19 est installée. L’ID de correctif est MDVA-35982. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le marchand ne peut pas envoyer certaines commandes.

<u>Étapes à reproduire</u>:

1. Sélectionnez n’importe quel site web de produit pour le produit, à l’exception de la boutique par défaut. Voir [Produit sur les sites web](https://docs.magento.com/user-guide/catalog/settings-basic-websites.html) pour obtenir des instructions détaillées.
1. Créez un rôle utilisateur pour l’administrateur avec des étendues de rôle personnalisées, dans lesquelles le site web/magasin par défaut n’est pas sélectionné. Voir [Définition d’un rôle](https://docs.magento.com/user-guide/system/permissions-user-roles.html#define-a-role) pour obtenir des instructions détaillées.
1. Ouvrez le produit en mode d’édition et définissez un Prix du groupe pour ce produit, dans **Tarifs avancés**. Voir [Prix du groupe](https://docs.magento.com/user-guide/catalog/product-price-group.html) pour obtenir des instructions détaillées.
1. Créez une commande avec ce produit.
1. Connectez-vous sous l’administrateur avec ce rôle d’utilisateur et créez une diffusion. Voir [Création d’un envoi](https://docs.magento.com/user-guide/sales/shipments-create.html) pour obtenir des instructions détaillées.

<u>Résultats attendus</u>:

L&#39;envoi est créé.

<u>Résultats réels</u>:

L&#39;erreur suivante s&#39;affiche :

`"0":"Notice: Undefined offset: XX in \/vendor\/magento\/module-catalog\/Model\/Product\/Attribute\/Backend\/GroupPrice\/AbstractGroupPrice.php on line 290"`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
