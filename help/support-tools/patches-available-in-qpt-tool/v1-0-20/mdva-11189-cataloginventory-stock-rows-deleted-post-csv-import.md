---
title: "MDVA-11189 : lignes cataloginventory_stock supprimées après importation CSV"
description: Le correctif MDVA-11189 Adobe Commerce corrige le problème après l’importation d’un fichier .csv pour mettre à jour le stock de produits, les lignes de la table `cataloginventory_stock` sont supprimées. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 est installé. L’ID de correctif est MDVA-1189. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.5.
exl-id: 84e1979c-826c-4c01-b0c7-8054bb4b23f0
feature: Catalog Management, Data Import/Export, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-11189 : lignes cataloginventory_stock supprimées après importation CSV

Le correctif Adobe Commerce MDVA-11189 corrige le problème après l’importation d’un fichier .csv pour mettre à jour le stock de produits, les lignes de la table `cataloginventory_stock` sont supprimées. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 est installé. L’ID de correctif est MDVA-1189. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.2.3

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce (toutes les méthodes de déploiement) 2.3.0-2.3.4-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Correction du problème qui se produisait lorsque, après l’importation d’un `.csv` pour mettre à jour le stock de produits, les lignes de la table `cataloginventory_stock` étaient supprimées.

<u>Étapes à reproduire :</u>

1. Dans la base de données, exécutez la commande MySQL suivante : `select count(*) from cataloginventory_stock_status;`
1. Notez le nombre de lignes.
1. Définissez crontab comme suit : `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. Accédez au panneau d’administration dans **Système** > **Outils** > **Gestion des index**.
1. Définissez les indexeurs sur *Mettre à jour par planification.*
1. Accédez à **Système** > *Transfert de données* > **Exporter**.
1. Définissez **Type d’entité** sur *Produits* > **Continuer**.
1. Ouvrez le fichier `.csv` enregistré > Supprimer toutes les colonnes, à l’exception de SKU et QTY.
1. Remplacez la quantité de tous les produits par 150.
1. Enregistrez le fichier `.csv`.
1. Accédez à **Système** > *Transfert de données* > **Importer** .
1. Définissez les valeurs suivantes :
   1. Type d’entité : *Products*
   1. Comportement d’importation : *Ajouter/Mettre à jour*
   1. Conservez toutes les autres valeurs par défaut.
   1. Sélectionnez Fichier pour sélectionner la feuille de calcul du produit catalogue.
1. Cliquez sur **Vérifier les données** > **Importer**. Il faut compter 5 à 10 minutes pour le faire passer.
1. Dans la base de données, exécutez la commande MySQL suivante :
   `select count(*) from cataloginventory_stock_status;`

<u>Résultat réel :</u>

Le nombre de lignes dans `cataloginventory_stock` est réduit après l’importation CSV pour mettre à jour le stock.

<u>Résultat attendu :</u>

Le nombre de lignes dans `cataloginventory_stock` doit rester le même après l’importation CSV pour mettre à jour le stock.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
