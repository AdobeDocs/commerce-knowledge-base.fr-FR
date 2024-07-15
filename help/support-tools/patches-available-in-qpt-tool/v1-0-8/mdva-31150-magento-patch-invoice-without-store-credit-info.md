---
title: 'MDVA-31150 : facture sans informations de crédit de magasin'
description: Le correctif MDVA-31150 corrige le problème de création d’une facture sans informations de crédit de magasin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 est installé. Veuillez noter que le problème sera corrigé dans Adobe Commerce version 2.4.2.
exl-id: 70c87b67-6449-4285-9679-cca81613aa72
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-31150 : facture sans informations de crédit de magasin

Le correctif MDVA-31150 corrige le problème de création d’une facture sans informations de crédit de magasin. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 est installé. Veuillez noter que le problème sera corrigé dans Adobe Commerce version 2.4.2.

## Produits et versions concernés

* Ce correctif a été conçu pour Adobe Commerce sur l’infrastructure cloud 2.3.5-p2.
* Le correctif est également compatible avec Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.0 à 2.3.5-p2 et 2.4.0 à 2.4.0-p1.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Après la commande de facture par l’API, les informations de solde client et de carte-cadeau utilisées ne sont pas présentes dans la facture.

<u>Étapes à reproduire</u>

1. Ajoutez un montant de crédit de magasin à un compte client : dans la barre latérale Admin, accédez à **Customers** > **Tous les clients.**
1. Recherchez l&#39;enregistrement du client et cliquez sur **Modifier** dans la colonne Action, puis sur **Stocker le crédit** > Mettre à jour le solde > **Enregistrer le client**.
1. Accédez à Storefront et ajoutez des produits au panier.
1. Effectuez une commande en appliquant le montant du crédit de la boutique ou de la carte-cadeau comme paiement partiel.
1. Créez une facture à l’aide de `REST API>POST>/rest/V1/order/1/invoice` avec la charge utile :    ```    { "capture": true, "items": [ { "extension_attributes": {}, "order_item_id": 3, "qty": 1 } ], "notify": true, "appendComment": true, "comment": { "extension_attributes": {}, "comment": "string", "is_visible_on_front": 0 }, "arguments": { "extension_attributes": {} }}    ```
1. Obtenez la facture qui vient d’être créée à l’aide de `REST API>GET>/rest/V1/invoices/1`.

<u>Résultat attendu</u>

Le crédit de la boutique et le solde des cartes-cadeaux sont renvoyés par l’appel API.

<u>Résultat réel</u>

Le crédit de magasin et le solde des cartes-cadeaux ne sont pas renvoyés par l’appel API.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
