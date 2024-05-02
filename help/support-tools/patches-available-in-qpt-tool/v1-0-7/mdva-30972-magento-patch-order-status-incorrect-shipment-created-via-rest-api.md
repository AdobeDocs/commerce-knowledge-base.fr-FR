---
title: '''MDVA-30972 : envoi incorrect de l''état de la commande créé via l''API REST'''
description: Le correctif MDVA-30972 résout le problème en raison duquel le statut de la commande est modifié de manière incorrecte lors de la création de l’expédition via l’API REST. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé.
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972 : envoi incorrect du statut de la commande créé via l&#39;API REST

Le correctif MDVA-30972 résout le problème en raison duquel le statut de la commande est modifié de manière incorrecte lors de la création de l’expédition via l’API REST. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.7 est installée.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 à 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsqu’une livraison partielle est créée à partir de l’administrateur via l’API REST pour une commande avec *Fraude présumée* l’état de la commande est remplacé par *Traitement*. Il devrait rester à *Fraude présumée*.

<u>Conditions préalables</u>:

* PayPal EC ou un autre mode de paiement en ligne est configuré.
* L’intégration pour l’API REST est configurée.

<u>Étapes à reproduire</u>:

1. Créez une commande comportant plusieurs éléments.
1. Connexion à **Administration** > **Ventes** > **Commandes**. Ouvrez l’ordre que vous venez de créer.
1. Sur la page des détails de la commande, faites défiler l’écran jusqu’à **Total de la commande**. Cliquez sur le bouton **État** et sélectionnez *Fraude présumée*. Cliquez ensuite sur le bouton **Envoyer le commentaire** bouton .
1. Vérifiez que la commande a *Fraude présumée* maintenant.
1. Créez une livraison pour un article à partir de la commande à l’aide de l’API REST :

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. Ouvrez à nouveau la commande dans Admin et vérifiez son état.

<u>Résultats attendus</u>:

* État de la commande = *Fraude présumée*.
* Le statut de la commande n&#39;est pas modifié si la même expédition est créée depuis l&#39;administrateur.

<u>Résultats réels</u>:

État de la commande = *Traitement*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
