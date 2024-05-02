---
title: 'Correctif ''MDVA-33281 : problèmes d''incohérence de l''inventaire'''
description: Le correctif MDVA-33281 corrige trois problèmes d’incohérence de l’inventaire. Cliquez sur les problèmes liés dans la section Problème pour voir les étapes à suivre pour reproduire ces erreurs. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 est installé.
exl-id: adba9728-6e42-467e-943d-cf8af0bec353
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Correctif MDVA-33281 : problèmes d’incohérence de l’inventaire

Le correctif MDVA-33281 corrige trois problèmes d’incohérence de l’inventaire. Cliquez sur les problèmes liés dans la section Problème pour voir les étapes à suivre pour reproduire ces erreurs. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.14 est installée.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le correctif corrige les problèmes d’incohérence de l’inventaire, tels que :

* **Erreur fatale PHP** en cours d’exécution `bin/magento inventory:reservation:list-inconsistencies` dans l’interface de ligne de commande en raison d’un type de paramètre de SKU incorrect.
* **Dupliquer les données** dans la liste des incohérences.
* **Nouvelle réservation** sera créé avant la commande passée (réalisation précédente basée sur la réservation après la commande passée). En cas d&#39;erreur lors du placement de la commande, une réservation supplémentaire sera ajoutée pour compenser.

>[!NOTE]
>
>Il existe également un correctif MDVA-30112 qui résout le problème lorsqu’il y a un nombre inattendu important de [incohérences de réservation](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) dans notre documentation destinée aux développeurs, dans le `inventory_reservation` table. Pour la solution, reportez-vous à la section [Correctif du Magento MDVA-30112 : incohérences de réservations en grand nombre](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md) dans notre base de connaissances de soutien.

## Erreur fatale PHP

<u>Étapes à reproduire</u>:

Erreur fatale PHP lors de l’exécution `bin/magento inventory:reservation:list-inconsistencies`.

Pour obtenir une liste des incohérences de réservation, connectez-vous au serveur de production et exécutez la commande suivante dans l’interface en ligne de commande (-r switch - raw output) :

<pre>Inventaire bin/magento:reservation:list-incohérences -r</pre>

<u>Résultats attendus</u>:

La liste des incohérences de réservation est créée. Ils sont renvoyés au format suivant :

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u>Résultats réels</u>:

PHP Fatal Error est généré.

## Dupliquer les données

Les données en double se trouvent dans la variable `inventory_reservation table`.

<u>Étapes à reproduire</u>:

Pour résoudre les incohérences de réservation, exécutez la commande suivante :

<pre>SELECT *, COUNT(*) DU GROUPE inventory_reserve PAR métadonnées, SKU, quantité HAVAVAVAVANT COUNT(*) &gt; 1</pre>

<u>Résultats attendus</u>:

Aucun doublon.

<u>Résultats réels</u>:

Il existe des doublons.

## Nouvelle réservation

<u>Étapes à reproduire</u>:

Nouvelle réservation créée avant la commande passée :

1. Importez la base.
1. Exécuter `bin/magento setup:upgrade` dans le terminal.
1. Répertorier les incohérences en exécutant `bin/magento inventory:reservation:list-inconsistencies        -i -r` dans le terminal.

<u>Résultats attendus</u>:

Pas de boucle et des résultats beaucoup plus rapides.

<u>Résultats réels</u>:

Les mêmes résultats s’affichent dans une boucle infinie, ou la commande échoue avec `memory_limit`, selon les paramètres système.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
