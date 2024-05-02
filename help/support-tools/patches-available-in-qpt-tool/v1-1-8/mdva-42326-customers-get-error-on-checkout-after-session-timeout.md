---
title: 'MDVA-42326 : les clients reçoivent une erreur lors de l’extraction après le délai d’expiration de la session'
description: Le correctif MDVA-42326 résout le problème où les clients reçoivent une erreur lors de l’extraction après le délai d’expiration de la session, même si le panier persistant est activé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 est installé. L’ID de correctif est MDVA-42326. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326 : les clients reçoivent une erreur lors de leur passage en caisse après expiration de la session.

Le correctif MDVA-42326 résout le problème où les clients reçoivent une erreur lors de l’extraction après le délai d’expiration de la session, même si le panier persistant est activé. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.8 est installée. L’ID de correctif est MDVA-42326. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients reçoivent une erreur lors de l’extraction après le délai d’expiration de la session, même si le panier persistant est activé.

<u>Conditions préalables</u>:

1. Accédez à **Config** > **Général** > **Web** > **Paramètres des cookies par défaut** > **Durée de vie du cookie** et définissez sur **120**.
1. Accédez à **Config** > **Clients** > **Configuration client** > **Options des clients en ligne** et définissez les deux valeurs sur **2**.
1. Accédez à **Config** > **Clients** > **Panier persistant** et définissez sur **Activer**.
1. Accédez à **Config** > **Ventes** > **Méthodes de paiement** et désactiver tous les modes de paiement, à l’exception de **Commande d’archivage/d’argent** (il doit être activé).

<u>Étapes à reproduire</u>:

1. Connectez-vous en tant que client et ajoutez des produits au panier.
1. Vérifiez le panier.
1. Patientez deux minutes (défini dans la condition préalable) ; la session doit expirer.
1. Cliquez sur **Accès à la caisse** et n’actualisez pas la page.
1. Passage en caisse en tant qu’invité, renseignez l’adresse de livraison et choisissez un mode de livraison.
1. Cliquez sur **Suivant**.
1. Sur le **Révision et paiements** page, cliquez sur **Passer commande**. Comme un seul mode de paiement est autorisé, le client doit pouvoir passer la commande sans sélectionner le mode de paiement.

<u>Résultats attendus</u>:

Le client doit pouvoir passer la commande.

<u>Résultats réels</u>:

Le client reçoit l’erreur suivante : *Échec de la validation des adresses : le format de l’email est incorrect*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
