---
title: "ACSD-45424 : Incorrection de la compensation de réservation créée après un remboursement partiel"
description: Le correctif ACSD-45424 corrige le problème où une compensation de réservation incorrecte est créée après un remboursement partiel. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 est installé. L’ID de correctif est ACSD-45424. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: 0676cfda-a28e-4a66-a75b-8a3fc5e22566
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# ACSD-45424 : compensation de réservation incorrecte créée après un remboursement partiel

Le correctif ACSD-45424 corrige le problème où une compensation de réservation incorrecte est créée après un remboursement partiel. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.17 est installée. L’ID de correctif est ACSD-45424. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une compensation de réservation incorrecte est créée après un remboursement partiel.

<u>Étapes à reproduire</u>:

1. Activez le mode de livraison en magasin.
1. Créez trois sources d’inventaire et assurez-vous que l’emplacement de récupération est actif dans chacune d’elles (source1, source2, source3).
1. Créez un nouveau stock et affectez les trois sources au nouveau stock.
   * Ce stock doit être affecté au site web principal.
1. Créez un produit simple, P3, et affectez-lui toutes les sources.
1. Ajoutez les quantités suivantes pour les sources du produit simple et activez les commandes en arrière-plan :
   * Source par défaut - 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. Ajoutez le produit simple au panier à partir de l’interface frontale et passez au formulaire d’expédition.
1. Sélectionnez &quot;source1&quot; comme emplacement d’expédition.
1. Exécutez la requête suivante dans la base de données :

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   Vous obtiendrez l’enregistrement de commande placé dans la variable `inventory_reservation` table. La quantité est 10, ce qui est correct.
1. Facturez cette commande à partir du serveur principal.
1. Créez maintenant une note de crédit pour un seul produit. NE PAS sélectionner la variable *Retour à Stock* .
1. Exécutez la même requête à partir de l’étape 8.

<u>Résultats attendus</u>:

Si vous n’avez pas sélectionné l’option *Retour à Stock* lors de la création de l’avoir, la variable `inventory_reservation` ne contiendra pas d’enregistrement correspondant à l’avoir de crédit.

<u>Résultats réels</u>:

Même si vous n’avez pas sélectionné le *Retour à Stock* au cours de la création de l’avoir, il ajoute un enregistrement à `inventory_reservation` table avec `creditmemo_created` type d’événement. En outre, l’enregistrement de note de crédit ajouté dans la variable `inventory_reservation` a une quantité de 10, même si vous avez créé l’avoir pour une seule quantité.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
