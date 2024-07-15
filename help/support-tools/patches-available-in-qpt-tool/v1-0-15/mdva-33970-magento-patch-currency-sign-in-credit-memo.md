---
title: 'Correctif MDVA-33970 : symbole de devise dans l’avoir sur le crédit'
description: Le correctif MDVA-33970 résout le problème en raison duquel un symbole dollar ($) s’affichait à la place de la devise localisée dans un avoir. Cela se produit lorsqu’une portée **Website** est utilisée pour un attribut **Price**.
exl-id: 47a03067-86ef-4a55-8c21-921781062b53
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Correctif MDVA-33970 : symbole de devise dans l’avoir sur le crédit

Le correctif MDVA-33970 résout le problème en raison duquel un symbole dollar ($) s’affichait à la place de la devise localisée dans un avoir. Cela se produit lorsqu’une plage **Website** est utilisée pour un attribut **Price**.

Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Conditions préalables</u> :

Dans cet exemple, les paramètres suivants sont utilisés :

* Il existe 2 sites web : chacun a une **boutique** et une **boutique vue**.
* La **configuration par défaut** a le dollar de Singapour comme **devise** (**magasins > Configuration > Général > Configuration de devise**) :
   * **Devise de base** = *Dollar de Singapour*
   * **Devise d’affichage par défaut** = *Dollar de Singapour*
   * **Devises autorisées** = *Dollar de Singapour*
* **Le site Web 1** a une **configuration par défaut**.
* **Le site Web 2** a le Ringgit malaisien comme **Devise** :
   * **Devise de base** = *Ringgit malaisien*
   * **Devise d’affichage par défaut** = *Ringgit malaisien*
   * **Devises autorisées** = *Ringgit malaisien*
* Accédez à **Magasins > Symboles de devise** et définissez :
   * **MYR (Ringgit malaisien)** = *RM*
   * **SGD (Dollar Singapour)** = *SGD* (**Utiliser la norme** = *Coché*)
* Il existe un **produit**.

<u>Étapes à reproduire</u> :

1. Effectuez une **commande** à partir du **site Web 2** (vous pouvez la configurer comme valeur par défaut afin d’éviter des paramètres supplémentaires).
1. Connectez-vous à **Admin**.
1. Ouvrez l’ordre nouvellement créé.
1. Vérifiez que le **Symbole de devise** = *RM*.
1. Créez une **facture**.
1. Vérifiez que le **symbole de devise** = *RM* dans la facture.
1. Créez un **Avoir de crédit**.
1. Vérifiez que le **Symbole de devise** ** ** = *RM* dans la **Note de crédit**.
1. Ouvrez l’onglet **Credit Memos** dans **Order**.
1. Vérifiez le **Symbole de devise** dans la grille.
1. Ouvrez **Ventes > Avoir de crédit**.
1. Vérifiez le **Symbole de devise** dans la grille.

<u>Résultats attendus</u> :

Le symbole monétaire localisé correct est utilisé, comme prévu.

<u>Résultats réels</u> :

Le signe dollar ($) est utilisé, même s’il n’est pas configuré dans les paramètres d’administration.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants, en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
