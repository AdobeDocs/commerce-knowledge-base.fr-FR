---
title: 'MDVA-37224 : impossible de payer un "devis négociable" avec PayFlow Pro'
description: Le correctif MDVA-37224 corrige le problème lorsque les clients ne sont pas en mesure de payer un **devis négociable** avec Paypal PayFlow Pro. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 est installé. L’ID de correctif est MDVA-37224. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.
exl-id: df75b38d-64c8-46b5-85ff-7606ce1dfd34
feature: B2B, Orders, Payments, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-37224 : Impossible de payer un &quot;devis négociable&quot; avec PayFlow Pro

Le correctif MDVA-37224 corrige le problème lorsque les clients ne sont pas en mesure de payer un **devis négociable** avec Paypal PayFlow Pro. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 est installé. L’ID de correctif est MDVA-37224. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

* Le correctif a été conçu pour Adobe Commerce sur l’infrastructure cloud 2.3.6-p1
* Le correctif est également compatible avec Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.3-2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Conditions préalables</u> :

* Adobe Commerce avec module B2B installé
* Fonctionnalité d’entreprise activée
* Fonctionnalité **Négociable Quote** activée
* Il existe un utilisateur de société
* Le mode de paiement PayPal PayFlow Pro est activé et configuré.
* Le mode de paiement PayPal PayFlow Pro est autorisé pour B2B
* 2 produits avec des prix différents ont été créés

<u>Étapes à reproduire</u> :

1. Ouvrez le storefront.
1. Ajoutez **Produit 1** au panier.
1. Créez une **citation négociable** pour **Produit 1**.
1. Ajoutez **Product 2** au panier.
1. À partir de l’administrateur, acceptez la **citation négociable** créée à l’étape 3.
1. À partir de Storefront, ouvrez cette **citation négociable** et passez en caisse.
1. Sélectionnez la **Méthode de paiement** = *PayPal PayFlow Pro* à l’étape **Révision et paiements** .
1. Placez la commande.

<u>Résultats attendus</u> :

* La commande est passée correctement, comme prévu.
* PayPal envoie un courrier électronique contenant les informations correctes au client, comme prévu.

<u>Résultats réels</u> :

* La page web se bloque et ne termine pas la commande.
* PayPal envoie une confirmation au client avec zéro valeur, comme dans cet exemple :

```php
Order ID: A1xxxxxxxxx
Order Placed: Monday, April 21, 2021 01:12:12 PM PDT

Shipping Amount: $0.00
Tax Amount: $0.00
Amount of Transaction: $0.00
Payment Type: Visa

BILL TO
--------
US
```


## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* 
   * [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
