---
title: 'ACSD-46520 : état de commande incorrect lors du remboursement à l’aide de crédits de magasin'
description: Cet article fournit une solution au problème où les utilisateurs obtiennent un état de commande incorrect lorsqu’ils sont remboursés à l’aide de crédits de magasin.
exl-id: 8464df22-0223-4ded-a15f-ce06eacdf77c
feature: Orders, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46520 : état de commande incorrect lors du remboursement à l’aide de crédits de magasin

Le correctif ACSD-46520 résout le problème où les utilisateurs obtiennent un état de commande incorrect lorsqu’ils sont remboursés à l’aide de crédits de magasin. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 est installé. L’ID de correctif est ACSD-46520. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 et 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs obtiennent un état de commande incorrect lorsqu’ils sont remboursés à l’aide de crédits de magasin.

<u>Étapes à reproduire</u> :

1. Créez un compte client sur le storefront et connectez-vous.
1. Attribuez des crédits de magasin au client à partir de l’administrateur. Les crédits de magasin devraient couvrir toute la commande.
1. Passez une commande à l’aide des crédits de magasin.
1. Facturez la commande.
1. Créez un avoir pour rembourser le montant total de la commande.
Cochez la case **[!UICONTROL Refund to store credit]** .
1. Vérifiez l’état de la commande.

<u>Résultats attendus</u> :

L’état de la commande est *Fermé*.

<u>Résultats réels</u> :

L’état de la commande est *Complete*, ce qui n’est pas l’état correct.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou [!DNL Magento Open Source] sur site : [Outils de correctifs de qualité > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide de l’outil de correctifs de qualité.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de l’outil Correctifs de qualité.
