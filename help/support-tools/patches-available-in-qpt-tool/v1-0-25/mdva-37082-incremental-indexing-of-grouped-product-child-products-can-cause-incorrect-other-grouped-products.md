---
title: "MDVA-37082 : Index partiel incorrect de l’état des stocks pour les produits groupés"
description: Le correctif du Magento MDVA-37082 corrige le problème lorsque l’index partiel de l’état des stocks pour les produits groupés est incorrect pour les stocks personnalisés. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 est installé. L’ID de correctif est MDVA-37082. Veuillez noter que le problème doit être corrigé dans Magento 2.4.4.
exl-id: 1c0abc99-bd24-4848-87a3-227a63655cb7
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-37082 : Index partiel incorrect de l’état des stocks pour les produits groupés

Le correctif du Magento MDVA-37082 corrige le problème lorsque l’index partiel de l’état des stocks pour les produits groupés est incorrect pour les stocks personnalisés. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.25 est installée. L’ID de correctif est MDVA-37082. Veuillez noter que le problème doit être corrigé dans Magento 2.4.4.


## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
Adobe Commerce sur l’infrastructure cloud 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :**
Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.0-2.4.2-p1
>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’indexation incrémentielle des produits enfants groupés peut entraîner une indexation incorrecte d’autres produits groupés incorrects lorsque des enfants sont partagés.

<u>Étapes à reproduire</u>:

* Créez un nouveau stock et une nouvelle source pour le site web principal.
* Créez 3 produits simples avec des quantités 10,15 et 0.
* Créez 2 produits regroupés et attribuez le premier produit simple avec la quantité 10 à l’un et 2 autres produits simples à l’autre.
* Vérifiez que les deux produits regroupés peuvent être accessibles depuis le front-end, en stock.
* Attribuez le produit simple avec la quantité 0 aux produits en vente anticipée du premier produit groupé.
* Nettoyez le cache de page complète et vérifiez le 2e produit groupé à partir du front-end.
* Exécutez une réindexation complète.
* Vérifiez le 2e produit groupé à partir du front-end.
* Enregistrez le premier produit groupé.
* Nettoyez le cache de la page complète et vérifiez le deuxième produit groupé à partir du front-end.

<u>Résultats attendus</u>:

Le produit groupé n’est pas en rupture de stock après avoir enregistré un autre produit groupé avec une vente incitative. Le problème est résolu après une réindexation complète.

<u>Résultats réels</u>:

Le 2e produit groupé est en rupture de stock lorsque vous enregistrez le 1er produit groupé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, suivez les liens suivants vers la documentation destinée aux développeurs, en fonction de votre méthode de déploiement Adobe Commerce :

* Adobe Commerce sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Vérifiez si le correctif est disponible pour votre problème de Magento à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
