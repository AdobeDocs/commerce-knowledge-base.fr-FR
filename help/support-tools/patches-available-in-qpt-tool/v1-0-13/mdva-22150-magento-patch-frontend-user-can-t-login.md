---
title: "MDVA-22150 Adobe Commerce patch : l’utilisateur front-end ne peut pas se connecter"
description: Le correctif MDVA-22150 résout le problème lorsqu’un utilisateur front-end ne peut pas se connecter après un achat abandonné à l’aide d’un bon. Cela se produit lorsqu’un utilisateur front-end utilise un code de bon sur un produit qui a été désactivé avant de terminer l’achat. En conséquence, l’utilisateur front-end ne peut plus se connecter et reçoit une erreur 503. Un autre effet de ce problème est que la capacité de gérer les paniers des clients dans l’administrateur cesse de fonctionner.
exl-id: 8aabe7b2-4b8a-4339-914e-7131006907b3
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Correctif MDVA-22150 Adobe Commerce : l’utilisateur front-end ne peut pas se connecter

Le correctif MDVA-22150 résout le problème lorsqu’un utilisateur front-end ne peut pas se connecter après un achat abandonné à l’aide d’un bon. Cela se produit lorsqu’un utilisateur front-end utilise un code de bon sur un produit qui a été désactivé avant de terminer l’achat. En conséquence, l’utilisateur front-end ne peut plus se connecter et reçoit une erreur 503. Un autre effet de ce problème est que la capacité de gérer les paniers des clients dans l’administrateur cesse de fonctionner.

Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.3.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.2

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce 2.3.1 - 2.3.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire :</u>

1. Connectez-vous à l’administrateur et créez un produit configurable.
1. Accédez à **Règles de panier** et créez un code de bon avec une remise.
1. Créez un compte client dans le front-end.
1. Ajoutez le produit au panier, suivez le processus de passage en caisse et saisissez le coupon.
1. Après avoir saisi le bon, n’envoyez pas la commande, mais abandonnez la commande et déconnectez-vous.
1. Revenez à l’ administrateur et désactivez l’ensemble du produit configurable.

<u>Résultats attendus :</u>

Le produit n’est pas affiché dans le panier sur Storefront, ni dans le message d’erreur approprié indiquant que le produit a été désactivé, comme prévu.

<u>Résultats réels :</u>

* Lorsque vous tentez de vous reconnecter à l’interface frontale, vous êtes coincé dans une boucle infinie (qui, à terme, affichera une exception après un long délai).
* La possibilité de gérer les paniers des clients dans l’administration cesse de fonctionner.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
