---
title: 'MDVA-29400 : Commandes en double passées avec paiement express PayPal'
description: Le correctif MDVA-29400 résout le problème de création de commandes dupliquées lorsque les clients passent des commandes avec PayPal Express Checkout. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 est installé. L’ID de correctif est MDVA-29400. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.1.
exl-id: 75b943c8-5f7c-4d94-ae92-935428fdfcf8
feature: Checkout, Orders, Payments
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-29400 : Commandes en double passées avec paiement express PayPal

Le correctif MDVA-29400 résout le problème de création de commandes dupliquées lorsque les clients passent des commandes avec PayPal Express Checkout. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 est installé. L’ID de correctif est MDVA-29400. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.1.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les commandes dupliquées sont créées lorsque les utilisateurs passent des commandes avec PayPal Express Checkout.

<u>Conditions préalables</u> :

Activation et configuration du paiement express PayPal.

<u>Étapes à reproduire</u> :

1. Ajoutez un produit au panier.
1. Accédez à la page Passage en caisse et utilisez PayPal Express comme mode de paiement.
1. Il redirigera vers la page paypal/express/review/.
1. Ordre de priorité. Vous serez redirigé vers la page de succès.
1. Revenez à la page PayPal/express/review/.
1. Cliquez sur le bouton **Passer commande** .

<u>Résultats attendus</u> :

Une seule commande est créée.

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante : *Le jeton de passage en caisse express PayPal n’existe pas*, mais la deuxième commande a bien été passée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
