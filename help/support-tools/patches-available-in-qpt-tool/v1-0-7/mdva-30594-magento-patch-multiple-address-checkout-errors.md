---
title: 'MDVA-30594 : plusieurs erreurs de passage en caisse'
description: Le correctif MDVA-30594 résout le problème en raison duquel le client ne voit pas la page de succès de la commande après avoir passé une commande avec plusieurs adresses. Si vous cochez les commandes sur l’administrateur Commerce, deux commandes portant les mêmes produits s’affichent au lieu des produits appropriés. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 7560cc39-ff0d-4313-979e-5cd588554c1d
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# MDVA-30594 : erreurs de passage en caisse de plusieurs adresses

Le correctif MDVA-30594 résout le problème en raison duquel le client ne voit pas la page de succès de la commande après avoir passé une commande avec plusieurs adresses. Si vous cochez les commandes sur l’administrateur Commerce, deux commandes portant les mêmes produits s’affichent au lieu des produits appropriés. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.3.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les commandes à plusieurs adresses ne sont pas terminées avec la page de succès des commandes et présentent deux commandes avec les mêmes produits au lieu des commandes correctes.

<u>Conditions préalables</u> :

Créez deux sites web avec des magasins et des vues de magasin.

<u>Étapes à reproduire</u> :

1. Définissez **Portée du prix du catalogue** pour le catalogue du site web (**Magasins** > **Paramètres** > **Configuration** > **Catalogue** > **Catalogue** > **Prix** > **Portée**).
1. Configurez les **Taxes sur les produits fixes (FPT)** (**Magasins** > **Configuration** > **Ventes** > **Taxe** > **Taxes sur les produits fixes**) :

   * **Activer FPT** = *Oui*
   * **Prix d’affichage dans la liste de produits** = *Exclure FPT*
   * **Prix d’affichage sur la page de consultation du produit** = *Exclure FPT*
   * **Prix d’affichage dans les modules de vente** = *Exclure FPT* (y compris la description **FPT** et le prix final).
   * **Prix d’affichage dans les emails** = *Exclure FPT* (y compris la description **FPT** et le prix final).
   * **Appliquer la taxe à FPT** = *Oui*
   * **Inclure FPT dans le sous-total** = *Non*

1. Créez un **attribut FPT** et affectez-le au jeu d’attributs par défaut. (Voir [Configuration FPT : création d’un attribut FPT](https://docs.magento.com/user-guide/tax/fixed-product-tax-configuration.html#step-2-create-an-fpt-attribute) dans notre guide d’utilisation).

1. Créez quatre produits simples et définissez la **FPT** **valeur d’attribut** (Exemple : définissez le **FPT**)   **valeur d’attribut** = *Australie*).

1. Créez deux produits regroupés avec la configuration suivante :

   * Définissez **FPT**.
   * Définissez **Dynamic Price** = *No*.
   * Définissez **Price** = *100*.
   * Les options de bundle sont proposées ensemble, toutes marquées comme valeur par défaut avec **Price Type** = *Fixed*.
   * Ajoutez deux des produits simples créés à l’étape 4.

1. Créez un compte d’utilisateur dans le front-end. Mettez à jour l’adresse avec l’adresse australienne (définissez le pays sur l’Australie ou n’importe quel pays a été utilisé dans la configuration **FPT**).

1. Ajoutez les deux produits regroupés au panier.

1. Accédez à la page du panier et vérifiez que le **FPT** s’affiche correctement.

1. Cliquez sur **Passage en caisse avec plusieurs adresses**.

1. Ajoutez une seconde adresse.

1. Attribuez chaque produit à une adresse différente.

1. Passez au processus de passage en caisse jusqu’à **Passer commande**.

1. Cliquez sur le bouton **Passer commande** .

<u>Résultats attendus</u> :

La commande comportant plusieurs adresses est passée avec succès.

<u>Résultats réels</u> :

Un message du type &quot;*Une erreur s’est produite.*&quot; s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
