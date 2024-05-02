---
title: "MDVA-28191 : Aucun mode de paiement pour un site web dans Admin Créer une commande"
description: Le correctif MDVA-28191 corrige le problème lorsqu’un mode de paiement ne se charge pas dans l’Admin **Créer une commande** pour un site web, bien que les méthodes de paiement puissent s’afficher pour d’autres sites web.  Ce correctif est disponible lorsque l’outil [Outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) version 1.0.5 est installé.
exl-id: 42169743-4f09-4f0a-aadd-931cccc9b467
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28191 : Aucun mode de paiement pour un site web dans Admin Créer une commande

Le correctif MDVA-28191 corrige le problème lorsqu’un mode de paiement ne se charge pas dans l’administrateur. **Créer une commande** pour un site web, bien que les méthodes de paiement puissent s’afficher pour d’autres sites web.  Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.5 de l’outil est installée.

## Produits et versions concernés

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.3 à 2.4.1 (y compris 2.3.5-p1).

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la création d’une commande à partir du serveur principal Adobe Commerce crée deux guillemets, l’un est inactif et l’autre est actif. Mais la session contient l’ID de guillemet inactif.

<u>Étapes à reproduire</u>

1. Accédez à **Panneau d’administration** > **Ventes** > **Commandes** et cliquez sur le bouton **Créer une commande** bouton .
1. Sélectionnez le client pour lequel vous souhaitez créer la commande.
1. Si votre boutique comporte plusieurs vues, sélectionnez la vue de magasin où la commande doit être placée, dans la variable **Créer une commande** pour l’utilisateur que vous avez sélectionné.
1. Ajoutez des produits à partir du **Activités du client** ou du catalogue en cliquant sur **Ajouter des produits**. Faites défiler la page vers le bas pour terminer les sections suivantes selon les besoins dans l’ordre :
   * Appliquer les codes de bon
   * Mode de paiement
   * Méthode d’expédition
   * Commentaires sur la commande

<u>Résultat attendu :</u>

Les modes de paiement doivent être chargés dans l’Admin de tous les sites Web.

<u>Résultat réel :</u>

Aucun mode de paiement n’est disponible (le message n’est pas non plus &quot;*Aucune information de paiement requise*&quot; affiché) pour ce site web, bien que les méthodes de paiement puissent s’afficher lors du test des commandes pour d’autres sites web.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
