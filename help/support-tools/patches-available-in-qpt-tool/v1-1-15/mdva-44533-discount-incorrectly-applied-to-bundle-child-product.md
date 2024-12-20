---
title: "MDVA-44533 : remise incorrectement appliquée au produit enfant groupé"
description: Le correctif MDVA-44533 corrige le problème lorsqu’une remise est incorrectement appliquée à un produit enfant groupé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 est installé. L’ID de correctif est MDVA-44533. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 84302ed4-d850-45e4-8b5b-44495f9df820
feature: Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-44533 : remise incorrectement appliquée au produit enfant groupé

Le correctif MDVA-44533 corrige le problème lorsqu’une remise est incorrectement appliquée à un produit enfant groupé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 est installé. L’ID de correctif est MDVA-44533. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La remise est incorrectement appliquée à un produit enfant regroupé.

<u>Étapes à reproduire</u> :

1. Créez un produit simple au prix de 50$.
1. Créez un produit groupé et affectez le produit simple comme seule option pour le produit groupé.
1. Créez une règle de prix de panier avec :

   * Condition : si le montant total est supérieur à 130$
   * Action : une remise de 10$ de montant fixe est appliquée

1. Accédez au storefront et ajoutez le produit du lot au panier avec qty = 1.
1. Allez dans le panier et vérifiez que le coût total du produit groupé est de 50$ et que la remise ne s&#39;applique pas.
1. Remplacez la quantité par 2 et mettez à jour le panier. Le coût total du produit groupé doit maintenant être de 100$.

<u>Résultats attendus</u> :

La remise n’est pas appliquée car le sous-total est de 100\$, qui est inférieur à 130\$ dans la condition de la règle.

<u>Résultats réels</u> :

La remise est appliquée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
