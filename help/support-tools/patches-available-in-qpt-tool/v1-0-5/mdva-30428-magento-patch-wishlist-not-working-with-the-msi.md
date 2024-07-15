---
title: 'MDVA-30428 : liste bloquée ne fonctionnant pas avec Inventory management'
description: Le correctif MDVA-30428 résout la liste des souhaits qui ne fonctionne pas avec Inventory management (MSI). Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 est installé.
exl-id: 79e8d5d6-b073-48cf-8ecc-5c44667c12ad
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-30428 : liste bloquée ne fonctionnant pas avec Inventory management

Le correctif MDVA-30428 résout la liste des souhaits qui ne fonctionne pas avec Inventory management (MSI). Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 est installé.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3 - 2.3.3-p1 (QPT 1.0.6) et 2.3.5 - 2.4.1 (QPT 1.0.5)

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de l’ajout d’un produit à une liste de souhaits, lorsque le produit est affecté à une source d’inventaire personnalisée, le message suivant indique : &quot;*Nous ne pouvons pas ajouter l’élément à la liste de souhaits maintenant : impossible d’ajouter un produit sans stock à la liste de souhaits.*&quot;

<u>Étapes à reproduire</u> :

1. Créez une source d’inventaire dans l’administrateur Commerce. Pour les étapes, reportez-vous à [Catalogue > Ajout d’une nouvelle Source](https://docs.magento.com/user-guide/catalog/inventory-sources-add.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=new%20inventory%20source) dans notre guide d’utilisation.
1. Créez un nouveau stock dans l’administrateur Commerce, puis affectez le nouveau stock et le site web par défaut au nouveau stock. Pour les étapes, consultez [Catalogue > Ajouter un nouveau stock](https://docs.magento.com/user-guide/catalog/inventory-stock-add.html#add-new-stock) dans notre guide d’utilisation.
1. Créez un produit simple et affectez uniquement le nouveau stock en tant qu’inventaire.
1. Visitez la page de détails du produit simple dans l’interface frontale.
1. Ajoutez le produit à la liste des souhaits. L’erreur suivante s’affiche : *Nous ne pouvons pas ajouter l’élément à la liste de souhaits pour l’instant : impossible d’ajouter un produit sans stock à la liste de souhaits*.

<u>Résultats attendus</u> :

Le produit doit être ajouté à la liste des souhaits avec le stock personnalisé.

<u>Résultats réels</u> :

Le produit n’est pas ajouté à la liste des souhaits et un message d’erreur s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
