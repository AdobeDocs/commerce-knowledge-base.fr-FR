---
title: "ACSD-54966 : correctif pour la réutilisation des codes de bons après les commandes en échec"
description: Appliquez le correctif ACSD-54966 pour résoudre le problème Adobe Commerce empêchant la réutilisation des codes de bons limités par promotion et par panier suite à une commande précédemment en échec.
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
exl-id: 931cfe7a-30a3-4a7d-ada5-4e2d7084f3e1
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-54966 : correctif pour la réutilisation des codes de coupon après les commandes en échec

Le correctif ACSD-54966 corrige le problème empêchant la réutilisation des codes de bons limités par client suite à une commande précédemment en échec. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.42 est installée. L’ID de correctif est ACSD-54966. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un code de bon, limité à un usage unique par client, ne peut pas être réutilisé suite à une commande précédente en échec.

<u>Étapes à reproduire</u>:

1. Configurez une règle de prix de panier avec *[!UICONTROL Uses per Customer]* = *1*.
1. Continuez pour effectuer un achat à l’aide du code de bon attribué.
1. Annulez la commande à partir du panneau d’administration ou exécutez la commande en cas d’échec de paiement.
1. Exécutez la commande : `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Essayez de passer une commande ultérieure en utilisant le même code de bon pour le même client.

<u>Résultats attendus</u>:

Après l’annulation de la commande ou l’échec de paiement, le client peut réutiliser le code de bon pour un nouvel achat.

<u>Résultats réels</u>:

Le client ne peut pas réutiliser le code de coupon.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
