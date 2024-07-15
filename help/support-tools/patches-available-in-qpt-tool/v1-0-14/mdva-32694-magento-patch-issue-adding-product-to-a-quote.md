---
title: 'Correctif MDVA-32694 : problème lors de l’ajout d’un produit à un guillemet'
description: Le correctif MDVA-32694 résout le problème de l’impossibilité d’ajouter un produit valide dans Admin à un devis négociable créé sur le site web non par défaut.
exl-id: 964abbbd-c8b1-4645-a393-7283f52e94ff
feature: Products, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Correctif MDVA-32694 : problème d’ajout d’un produit à un guillemet

Le correctif MDVA-32694 résout le problème de l’impossibilité d’ajouter un produit valide dans Admin à un devis négociable créé sur le site web non par défaut.

Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.2 avec B2B version 1.2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Conditions préalables</u> :

Installez une nouvelle instance Adobe Commerce avec B2B.

<u>Étapes à reproduire</u> :

1. Accédez à **STORES > Configuration > GÉNÉRAL > Fonctionnalités B2B** et activez **Société** et **Guillemet B2B**.
1. Créez 2 autres sites web avec **stores** et **storeviews** (Au total, vous devriez avoir 3 sites web : *base*, *site web2*, *site web3*).
1. Créez un produit simple et affectez-le uniquement à *website3*.
1. Accédez à **STORES > All Stores** et définissez *website3* sur **default**.
1. Accédez à l&#39;interface et créez une nouvelle société sur *site web3*.
1. Ajoutez le produit créé précédemment au panier et créez un nouveau guillemet négociable.
1. Accédez à **STORES > All Stores** et redéfinissez le site Web &quot;*base*&quot; en **default**.
1. Accédez à **SALES > Guillemets > Ouvrir le guillemet créé précédemment** et essayez d’y ajouter le même produit.

<u>Résultats attendus</u> :

L’utilisateur administrateur peut ajouter le même produit au devis, comme prévu.

<u>Résultats réels</u> :

L’utilisateur administrateur ne peut pas ajouter le même produit au guillemet, et ce message d’erreur s’affiche :

```php
This product is assigned to another website.
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
