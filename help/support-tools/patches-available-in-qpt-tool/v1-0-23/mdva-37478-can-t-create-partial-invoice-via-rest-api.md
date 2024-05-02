---
title: "MDVA-37478 : impossible de créer une facture partielle via l'API REST"
description: Le correctif MDVA-37478 corrige le problème lorsque vous ne parvenez pas à créer une facture partielle via l'API REST pour une commande passée avec le mode de paiement **Paiement sur compte**. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 est installé. L’ID de correctif est MDVA-37478. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.
exl-id: 1b235baa-a188-467c-8ae5-de0836bc2caa
feature: REST, B2B, Invoices
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-37478 : impossible de créer une facture partielle via l&#39;API REST

Le correctif MDVA-37478 corrige le problème lorsque vous ne parvenez pas à créer une facture partielle via l&#39;API REST pour une commande passée avec le mode de paiement. **Paiement sur compte**. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.23 est installée. L’ID de correctif est MDVA-37478. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

* Le correctif a été conçu pour Adobe Commerce sur l’infrastructure cloud 2.3.3-p1
* Le correctif est également compatible avec Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.0-2.3.7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Condition requise</u>:

Adobe Commerce avec module B2B installé

<u>Étapes à reproduire</u>:

1. Activer **Société B2B**.
1. Activer **Paiement sur compte** mode de paiement.
1. Créez 2 produits simples.
1. Créez un compte de société.
1. Ajoutez des crédits de la société dépassant le prix total de 2 produits créés.
1. Connectez-vous au front-end à l’aide du compte d’entreprise créé.
1. Ajoutez les 2 produits créés dans le panier, puis effectuez un passage en caisse à l’aide du **Paiement sur compte** mode de paiement.
1. Essayez de créer une facture partielle pour la commande créée via l&#39;API REST :

   ```php
   POST /rest/V1/order//invoice
   {
     "items": [
       {
         "order_item_id": 2,
         "qty": 1
       }
     ]
   }
   ```

<u>Résultats attendus</u>:

La facture partielle est créée pour une commande passée à l&#39;aide du **Paiement sur compte** mode de paiement, comme prévu.

<u>Résultats réels</u>:

L’erreur suivante est renvoyée par l’API REST :

```php
{"message":"Invoice Document Validation Error(s):\nAn invoice for partial quantities cannot be issued for this order. To continue, change the specified quantity to the full quantity."}
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants, en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
