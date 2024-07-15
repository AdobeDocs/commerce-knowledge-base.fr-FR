---
title: '''MDVA-39153 : le montant de la remise est mal calculé lors d''une réorganisation dans l''administrateur'''
description: Le correctif MDVA-39153 corrige le problème en raison duquel le montant de la remise est mal calculé lors d’une réorganisation dans l’Admin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 est installé. L’ID de correctif est MDVA-39153. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: d4d11bea-a528-4eb5-8a57-8a7330975e4a
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-39153 : Le montant de la remise est mal calculé lors d&#39;un réorganisation dans l&#39;Admin

Le correctif MDVA-39153 corrige le problème en raison duquel le montant de la remise est mal calculé lors d’une réorganisation dans l’Admin. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 est installé. L’ID de correctif est MDVA-39153. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le montant de la remise est mal calculé lors d&#39;un nouvel ordre dans l&#39;Admin.

<u>Étapes à reproduire</u> :

1. Accédez à **Admin** > **Magasins** > **Configuration** > **Ventes** > **Taxes**.
1. Activez la taxe pour l’expédition affichant la taxe dans le panier.
1. Activez et configurez la méthode d’expédition Taux de tableau (15 $).
1. Créez une règle de taxe pour le taux de taxe intégré (pour CA).
1. Créez une règle de prix de panier avec une remise fixe de 5 $ appliquée à l’ensemble du panier et du montant d’expédition.
1. Ajoutez un produit au prix de 12 € au panier et accédez à la page Panier.
1. Appliquez la remise au panier.
1. Définissez le mode de livraison dans la section &quot;Estimations&quot; sur &quot;Taux plat&quot;.
1. Passez en caisse jusqu’aux étapes de révision (ne pas passer la commande).
1. Accédez à la page d’accueil, puis revenez au panier.
1. Remplacez le mode de livraison dans la section &quot;Estimations&quot; par &quot;Taux de la table&quot;.

<u>Résultats attendus</u> :

La remise reste la même : 5 $.

<u>Résultats réels</u> :

La remise est de 6,31 $.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
