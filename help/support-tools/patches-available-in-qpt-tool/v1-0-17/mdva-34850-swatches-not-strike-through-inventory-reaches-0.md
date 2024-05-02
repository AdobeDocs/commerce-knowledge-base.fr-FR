---
title: '''MDVA-34850 : l’inventaire des échantillons non frappés atteint "0"'
description: Le correctif MDVA-34850 corrige le problème en raison duquel les échantillons ne sont pas tronqués lorsque l’inventaire atteint "0" et ne sont pas visibles dans le lien Page de détails du produit (PDP) vers aucun autre échantillon In-Stock. L’option **Afficher les produits en rupture de stock** est également définie sur *Oui* dans la configuration d’administration. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: 90f5cef4-137a-426d-a447-2d1aca23e6c1
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# MDVA-34850 : l’inventaire des échantillons non frappés atteint &quot;0&quot;

Le correctif MDVA-34850 corrige le problème en raison duquel les échantillons ne sont pas tronqués lorsque l’inventaire atteint &quot;0&quot; et ne sont pas visibles dans le lien Page de détails du produit (PDP) vers aucun autre échantillon In-Stock. La variable **Afficher les produits en rupture de stock** est également défini sur *Oui* dans la configuration admin. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.17 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.1 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les options de produit en rupture de stock ne s’affichent pas sur la page PDP lorsque le stock de stock par défaut n’est pas en cours d’utilisation et que **Afficher les produits en rupture de stock** est activée.

<u>Conditions préalables</u>:

* Installez le stock multi-source (MSI).
* Activer l’affichage des produits en rupture de stock dans [Options Stock](https://docs.magento.com/user-guide/configuration/catalog/inventory.html).

<u>Étapes à reproduire</u>:

1. Créez un stock de stock \[Nouveau stock\], en lui attribuant tous les sites web ainsi que la source ci-dessus. Désormais, le stock par défaut ne doit pas être en cours d’utilisation.
1. Créez un [produit configurable](https://docs.magento.com/user-guide/catalog/product-create-configurable.html) ajout de trois options de taille \[S,M,L\].
1. Ouvrez chaque option et ajoutez des quantités en attribuant uniquement la source personnalisée \[new\_source\] créée. Définissez également \[État source\] sur \[En stock\].
1. Réindexez et vérifiez le produit configurable à partir du front-end. Les trois options doivent être visibles.
1. Ouvrez un produit simple affecté à \[taille:S\] à partir du serveur principal et définissez \[état source\] sur \[état en rupture de stock\], mettez également la quantité à 0. Réindexez et vérifiez le produit configurable à partir du front-end.

<u>Résultats attendus</u>:

Puisque l’option Afficher les produits en rupture de stock est activée, les trois options doivent s’afficher. L’option En rupture de stock \[S\] doit être désactivée et ignorée. Il doit afficher 2 x sur 1 option produit avec prix = 12x2 dans les détails de commande sur le serveur frontal et le serveur principal.

<u>Résultats réels</u>:

L’option Stock épuisé est masquée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
