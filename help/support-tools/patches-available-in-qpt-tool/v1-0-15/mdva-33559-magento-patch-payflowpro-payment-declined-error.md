---
title: 'Correctif MDVA-33559 : le paiement PayflowPro a refusé l’erreur'
description: Le correctif MDVA-33559 résout le problème de refus des paiements PayPal PayflowPro.
exl-id: aec57ffa-07c7-404e-985d-8ec4fdb019b1
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Correctif MDVA-33559 : le paiement de PayflowPro a refusé l’erreur

Le correctif MDVA-33559 résout le problème de refus des paiements PayPal PayflowPro.

Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.15 est installée. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le problème concerne les caractères spéciaux esperluette (&amp;) et signe égal (=) utilisés dans les noms.

<u>Étapes à reproduire</u>:

1. Ajoutez un produit simple au panier.
1. Allez à la caisse.
1. Définissez l’adresse de livraison. (Exemple d’adresse de livraison : **Prénom** = ** *John&#39;s* **  **Nom** = ** *Apples &amp; Oranges, Inc* **  **Adresse postale** = *1234 E Nameless St*  **Pays** = *US*  **Etat/Province** = *Anystate*  **Ville** = *Anytown*  **Zip** = *12345*  **Téléphone** = *1234567890*)
1. Définir le paiement sur **PayPal PayflowPro** et essayer de terminer le passage en caisse.

<u>Résultats attendus</u>:

La transaction génère un paiement réussi ou un message d’erreur correct, comme prévu.

<u>Résultats réels</u>:

La transaction est refusée et le client reçoit un courrier électronique lui indiquant que la transaction a été refusée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants, en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
