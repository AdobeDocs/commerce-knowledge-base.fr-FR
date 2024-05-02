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

Le correctif MDVA-33970 résout le problème en raison duquel un symbole dollar ($) s’affichait à la place de la devise localisée dans un avoir. Cela se produit lorsqu’une **Site Web** est utilisée pour une **Prix** attribut.

Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.15 est installée. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Conditions préalables</u>:

Dans cet exemple, les paramètres suivants sont utilisés :

* 2 sites web existent ; chacun a une **Magasin** et un **Affichage en magasin**.
* La variable **Configuration par défaut** a le dollar de Singapour comme **Devise** (**Magasins > Configuration > Général > Configuration de devise**) :
   * **Devise de base** = *Singapour, dollars*
   * **Devise d’affichage par défaut** = *Singapour, dollars*
   * **Devises autorisées** = *Singapour, dollars*
* **Site web 1** a une **Configuration par défaut**.
* **Site 2** a le ringgit malaisien comme **Devise**:
   * **Devise de base** = *Malaisie, ringgit*
   * **Devise d’affichage par défaut** = *Malaisie, ringgit*
   * **Devises autorisées** = *Malaisie, ringgit*
* Accédez à **Magasins > Symboles de devise** et Définissez :
   * **MYR (Ringgit malaisien)** = *RM*
   * **SGD (dollar de Singapour)** = *SGD* (**Utilisation standard** = *Cochée*)
* Certains **Produit** existe.

<u>Étapes à reproduire</u>:

1. Effectuez une **Commande** de la **Site 2** (vous pouvez le configurer comme Par défaut afin d’éviter tout paramétrage supplémentaire).
1. Connexion à **Administration**.
1. Ouvrez l’ordre nouvellement créé.
1. Vérifiez que la variable **Symbole de devise** = *RM*.
1. Créez un **Facture**.
1. Vérifiez que la variable **Symbole de devise** = *RM* dans la facture.
1. Créez un **Crédit**.
1. Vérifiez que la variable **Symbole de devise**  ** ** = *RM* dans le **Crédit**.
1. Ouvrez le **Avoir** dans **Commande**.
1. Vérifiez les **Symbole de devise** dans la grille.
1. Ouvrir **Ventes > Avoir**.
1. Vérifiez les **Symbole de devise** dans la grille.

<u>Résultats attendus</u>:

Le symbole monétaire localisé correct est utilisé, comme prévu.

<u>Résultats réels</u>:

Le signe dollar ($) est utilisé, même s’il n’est pas configuré dans les paramètres d’administration.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants, en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
