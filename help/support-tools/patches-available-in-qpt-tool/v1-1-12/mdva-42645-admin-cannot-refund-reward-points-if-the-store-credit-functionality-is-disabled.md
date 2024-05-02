---
title: "MDVA-42645 : L'administrateur ne peut pas rembourser les points de récompense pour le crédit de magasin désactivé"
description: Le correctif MDVA-42645 résout le problème où l’administrateur ne peut pas rembourser les points de récompense si la fonctionnalité de crédit de magasin est désactivée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID de correctif est MDVA-42645. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 8e8f8c07-c1a2-4031-a2fb-cb737165dc2c
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-42645 : L’administrateur ne peut pas rembourser les points de récompense pour le crédit de magasin désactivé

Le correctif MDVA-42645 résout le problème où l’administrateur ne peut pas rembourser les points de récompense si la fonctionnalité de crédit de magasin est désactivée. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.12 est installée. L’ID de correctif est MDVA-42645. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’administrateur ne peut pas rembourser les points de récompense si la fonctionnalité de crédit de magasin est désactivée.

<u>Étapes à reproduire</u>:

1. Créez un produit simple.
1. Créez un compte client et ajoutez des points de récompense.
1. Désactivez la fonctionnalité de crédit de magasin en accédant à **Magasin** > Paramètres > **Configuration** > **Client** > **Configuration client** > **Options de crédit de magasin**.
1. Connectez-vous en tant que client auquel les points de récompense sont attribués.
1. Ajoutez un produit au panier et accédez au passage en caisse.
1. Utilisez les points de récompense de la section paiement et passez votre commande.
1. Ouvrez la commande dans l&#39;administrateur et facturez-la.
1. Cliquez sur le bouton **Crédit** lien pour créer une note de crédit.
1. Cochez l’option Rembourser les points de récompense en bas de l’écran et cliquez sur le bouton **Remboursement hors ligne**.

<u>Résultats attendus</u>:

* La note de crédit a été créée.
* Les points de récompense sont remboursés avec succès.

<u>Résultats réels</u>:

Le message d’erreur suivant s’affiche : *Vous ne pouvez pas utiliser plus de crédit de magasin que le montant de la commande.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
