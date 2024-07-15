---
title: 'MDVA-30112 : incohérences de réservation d’un grand nombre'
description: Le correctif MDVA-30112 résout le problème en raison duquel un grand nombre inattendu de [incohérences de réservation](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) se trouve dans la table `inventory_reservation`. Les incohérences de réservation incluent les commandes ouvertes non enregistrées et les commandes terminées qui ne sont pas enregistrées. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.2.
exl-id: db74fb61-dfeb-4e99-8513-d36fd68d2267
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# MDVA-30112 : incohérences de réservation d’un grand nombre

Le correctif MDVA-30112 résout le problème du nombre inattendu d’incohérences [ de réservation ](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) dans la table `inventory_reservation`. Les incohérences de réservation incluent les commandes ouvertes non enregistrées et les commandes terminées qui ne sont pas enregistrées. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.3.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La valeur [bunch-size](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#list-inconsistencies-command) est la valeur du nombre de commandes à charger simultanément. Lorsqu’il y a plus de commandes que cette valeur, Adobe Commerce considère les commandes dont le statut est en attente comme des incohérences.

>[!NOTE]
>
>Il existe un correctif MDVA-33281 qui corrige trois autres problèmes d’incohérence de l’inventaire. Cela inclut une erreur fatale PHP lors de l’exécution de `bin/magento inventory:reservation:list-inconsistencies` dans l’interface de ligne de commande. Un autre problème qui a été corrigé est la duplication des données dans la liste des incohérences. En outre, le problème où une réservation est créée avant le passage de la commande (réalisation précédente basée sur la réservation après la commande passée). Pour la solution, reportez-vous à [MDVA-33281 : problèmes d’incohérence de l’inventaire](/help/support-tools/patches-available-in-qpt-tool/v1-0-14/mdva-33281-magento-patch-inventory-inconsistency-issues.md) dans notre base de connaissances de support.

<u>Conditions préalables</u> :

Vous exécutez la commande suivante dans l’interface de ligne de commande pour répertorier les incohérences de réservation dans la table `inventory_reservation` :

```
magento inventory:reservation:list-inconsistencies
```

Vous constatez un nombre inattendu d’incohérences de réservation et/ou la commande ne s’exécute jamais.

<u>Étapes à reproduire</u> :

1. Exécutez la commande suivante dans l’interface de ligne de commande pour résoudre les incohérences :

   ```
   bin/magento inventory:reservation:list-inconsistencies -r | bin/magento inventory:reservation:create-compensations
   ```

1. Effectuez trois commandes :
   * Attribuez à chacun un seul produit.
   * Utilisez le mode de paiement Vérification/Commande d’argent, de sorte que l’état de la commande sera &quot;en attente&quot;.
1. Vous pouvez voir trois enregistrements avec -1 quantité dans la table `inventory_reservation`. Exécutez la commande suivante dans l’interface de ligne de commande pour afficher les incohérences :

   ```
   bin/magento inventory:reservation:list-inconsistencies
   ```

   Cela ne renvoie aucun résultat, ce qui est correct.

1. Exécutez la commande suivante dans l’interface de ligne de commande :

   ```
   Execute bin/magento inventory:reservation:list-inconsistencies      --bunch-size 1
   ```

   Les commandes d’état &quot;en attente&quot; s’affichent sous la forme d’incohérences.

1. Exécutez la commande suivante dans l’interface de ligne de commande :

   ```
   bin/magento inventory:reservation:list-inconsistencies      -r --bunch-size 1 | bin/magento inventory:reservation:create-compensations
   ```

<u>Résultats attendus</u> :

Adobe Commerce ne doit pas résoudre les incohérences des commandes d’état &quot;en attente&quot;. Les incohérences des stocks doivent être résolues pour les commandes dont les statuts sont &#39;terminé&#39;, &#39;fermé&#39; et &#39;annulé&#39;.

<u>Résultats réels</u> :

Lorsqu’il existe des commandes supérieures à la valeur de taille de lot spécifiée, Adobe Commerce considère les commandes dont le statut est &quot;en attente&quot; comme des incohérences et ajoute plusieurs incohérences en résolvant les enregistrements pour la même commande.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
