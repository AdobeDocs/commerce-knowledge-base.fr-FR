---
title: 'ACSD-55241 : **Used** et **Times Used** les attributs affichent des valeurs incorrectes pour les bons générés'
description: Appliquez le correctif ACSD-55241 pour résoudre le problème Adobe Commerce en raison duquel les attributs **Used** et **Times Used** affichent des valeurs incorrectes pour les bons générés
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: f830486ab3b00fca92dda897bbf0bfbae41543c1
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241 : **Used** et **Times Used** les attributs affichent des valeurs incorrectes pour les bons générés

Le correctif ACSD-55241 corrige le problème en raison duquel les attributs **Used** et **Times Used** affichent des valeurs incorrectes pour les bons générés. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.47 est installé. L’ID de correctif est ACSD-55241. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les attributs **Used** et **Times Used** affichent des valeurs incorrectes pour les bons générés.

<u>Étapes à reproduire</u> :

1. Créez **[!UICONTROL Cart Price Rules]** à partir de **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** et ajoutez toute condition qui correspond lors du placement d’une commande (par exemple : sous-total supérieur à *5$*).

   * Appliquez n’importe quelle remise.
   * Sélectionnez **[!UICONTROL Auto Coupon]**.
   * Il génère quelques codes de bon à partir de **Gérer les codes de bon**.
   * Réindexez et nettoyez le cache.

1. Créez un **[!UICONTROL customer account]** et connectez-vous au front-end.
1. Ajoutez un produit avec plus de *2* quantités dans le panier et appliquez un coupon.
1. Cliquez sur **[!UICONTROL Check Out with Multiple Addresses]**.
1. Sélectionnez une adresse distincte pour chaque quantité, passez la commande et effectuez le processus de passage en caisse.
1. Observez le total de la commande auprès de l’administrateur et consultez la remise appliquée.
1. Passez une autre commande avec un autre coupon.
1. Exécutez la commande `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` pour mettre à jour l’utilisation du code de coupon.

<u>Résultats attendus</u> :

Le nombre correct doit être affiché dans les colonnes **Durée d’utilisation** et **Utilisé** avec la valeur **Oui** pour **[!UICONTROL manage coupon]** dans l’élément **[!UICONTROL cart price rule]** de l’administrateur.

<u>Résultats réels</u> :

Le nombre de codes de coupon utilisé n’est pas mis à jour dans la colonne **Durée d’utilisation** de la grille des coupons, et la colonne **Utilisé** affiche la valeur *Non* si vous passez une commande avec plusieurs adresses de livraison.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
