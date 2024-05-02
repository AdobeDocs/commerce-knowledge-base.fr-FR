---
title: "MDVA-34943 : la commande rapide ne peut pas ajouter plus de 2 produits au panier"
description: Le correctif MDVA-34943 résout le problème lorsqu’une commande rapide ne permet pas d’ajouter plusieurs produits au panier. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.2.
exl-id: fcff6a78-fe00-4352-b0bc-149bd411d999
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# MDVA-34943 : la commande rapide ne peut pas ajouter plus de 2 produits au panier.

Le correctif MDVA-34943 résout le problème lorsqu’une commande rapide ne permet pas d’ajouter plusieurs produits au panier. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.17 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.0-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas ajouter rapidement deux ou plusieurs produits au panier.

<u>Conditions préalables</u>:

Adobe Commerce avec des produits simples.

<u>Étapes à reproduire</u>:

1. Accédez à **Ordre rapide** sur le storefront (lorsqu’il n’est pas connecté).
1. Saisissez un SKU valide, cliquez sur le produit qui apparaît dans le champ de saisie semi-automatique, puis définissez **Quantité** = *1*.
1. Saisissez le même SKU valide, mais modifiez la casse (en majuscules ou en majuscules) du premier caractère, puis cliquez sur le produit qui apparaît dans le champ de saisie automatique et définissez **Quantité** = *1*.
1. Saisissez un `random_sting_value` pour **SKU**, et définissez **Quantité** = *1*.
1. Définir **SKU** = *123123123*, et définissez **Quantité** = *1*.
1. Supprimez tout, à l’exception de la première entrée que vous avez ajoutée au **Ordre rapide** page.
1. Saisissez le premier SKU (similaire à l’étape 2 ci-dessus) dans la variable **Saisie de plusieurs SKU** puis cliquez sur **Ajouter à la liste**.
1. Cela se traduit par une quantité de 2 pour le premier SKU et une ligne pour un `random_sting_value`.
1. Pour tester davantage, actualisez la page.
1. Aucun SKU n’est ainsi généré pour une commande rapide, comme prévu.
1. Saisissez un `random_sting_value2` dans la **Saisie de plusieurs SKU** puis cliquez sur **Ajouter à la liste**.
1. Cela se traduit par deux SKU valides d’avant et une `random_sting_value2`.

<u>Résultats attendus</u>:

Au moins deux produits peuvent être ajoutés au panier, comme prévu.

<u>Résultats réels</u>:

Lorsque vous êtes dirigé vers la fonction **Panier** , le premier produit ajouté s’affiche normalement, mais pour le deuxième produit et tous les produits ajoutés au panier suivants, un &quot;*1 produit nécessite votre attention*&quot; s’affiche. Le deuxième ou tout autre produit sera répertorié dans la liste **Le produit nécessite de l’attention** de la **Panier** page.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
