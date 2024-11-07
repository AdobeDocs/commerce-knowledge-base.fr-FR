---
title: 'MDVA-42855 : la nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse '
description: Le correctif MDVA-42855 corrige le problème en raison duquel la nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID de correctif est MDVA-42855. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 37fc51f4-773e-4bef-9fb1-e6629562b94a
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-42855 : La nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse

Le correctif MDVA-42855 corrige le problème en raison duquel la nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID de correctif est MDVA-42855. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse.

<u>Étapes à reproduire</u> :

1. Créez un compte client et mettez à jour l’adresse de livraison et de facturation par défaut.
1. Ajoutez un produit au panier et accédez à la page de passage en caisse.
1. Sur l’expédition, cliquez sur **+ Nouvelle adresse**.
1. Saisissez votre nouvelle adresse et cochez la case **Enregistrer dans le carnet d’adresses** .
1. Sur paiement, cochez la case **Mon adresse de facturation et de livraison sont les mêmes** .
1. Placez la commande.
1. Vérifiez le carnet d&#39;adresses.

<u>Résultats attendus</u> :

La nouvelle adresse de livraison est enregistrée dans le carnet d’adresses.

<u>Résultats réels</u> :

La nouvelle adresse de livraison n’est pas enregistrée dans le carnet d’adresses.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
