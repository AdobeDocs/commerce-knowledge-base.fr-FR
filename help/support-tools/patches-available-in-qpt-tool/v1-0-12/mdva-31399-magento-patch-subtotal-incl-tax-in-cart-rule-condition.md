---
title: 'Correctif ''MDVA-31399 : Sous-total (Incl. Taxe) dans la condition de règle du panier"'
description: Le correctif MDVA-31399 ajoute le *Sous-total (Incl. Taxe)* option sur [condition de règle de prix du panier](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), corrigeant le problème lorsqu’il était impossible d’appliquer une règle de prix du panier basée sur Sous-total (Incl. Tax) number. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 est installé.
exl-id: ea0f4060-753a-4b0d-896b-fff54ffd1a82
feature: Marketing Tools, Orders, Shopping Cart, Taxes
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Correctif MDVA-31399 : Sous-total (Incl. Taxe) dans la condition de règle du panier

Le correctif MDVA-31399 ajoute le *Sous-total (Incl. Taxe)* sur [condition de règle de prix du panier](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), en corrigeant le problème lorsqu’il était impossible d’appliquer une règle de prix du panier basée sur le sous-total (Incl. Tax) number. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 est installé.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.2 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Il est impossible d&#39;appliquer une règle de prix de panier basée sur le sous-total (Incl. Tax) number.

<u>Étapes à reproduire</u> :

1. Configurez le prix du produit pour inclure la taxe.
1. Créez une règle fiscale et un taux d’imposition de 20 %.
1. Créez un produit avec **Price** = *100* (ce prix inclut la taxe).
1. Créez une nouvelle règle de prix de panier avec un coupon &quot;10off&quot; pour appliquer une remise fixe de 10 $ si le sous-total correspond à ces conditions :

**Conditions** : *Si TOUTES ces conditions sont TRUE :*        * **Sous-total** égal ou supérieur à 100.*

<u>Résultats attendus</u> :

Il est possible de créer une règle de prix de sous-total du panier avec un coupon afin d’appliquer une remise au sous-total, y compris la taxe.

<u>Résultats réels</u> :

Il existe deux options dans les conditions des règles de panier : *Sous-total* et *Sous-total (Excel). Taxe)*, et quelle que soit l’option sélectionnée, la règle s’applique uniquement au sous-total hors taxe.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
