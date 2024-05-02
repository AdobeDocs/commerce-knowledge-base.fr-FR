---
title: 'ACSD-55241 : **Used** et **Times Used** les attributs affichent des valeurs incorrectes pour les bons générés'
description: Appliquez le correctif ACSD-55241 pour résoudre le problème Adobe Commerce en raison duquel les attributs **Used** et **Times Used** affichent des valeurs incorrectes pour les bons générés
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: 5d0b4743fe49d22c099102490f93dc4065ab4413
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241 : **Utilisé** et **Heures utilisées** Les attributs affichent des valeurs incorrectes pour les bons générés

Le correctif ACSD-55241 corrige le problème en raison duquel la variable **Utilisé** et **Heures utilisées** Les attributs affichent des valeurs incorrectes pour les bons générés. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.47 est installée. L’ID de correctif est ACSD-55241. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

**Utilisé** et **Heures utilisées** Les attributs affichent des valeurs incorrectes pour les bons générés.

<u>Étapes à reproduire</u>:

1. Créer **[!UICONTROL Cart Price Rules]** de **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** et ajouter toute condition qui correspond lors du placement de la commande (par exemple : sous-total supérieur à *5$*)

* Appliquez n’importe quelle remise.
* Sélectionner **[!UICONTROL Auto Coupon]**.
* Il génère quelques codes de bon à partir de **Gestion des codes de bon**.
* Réindexez et nettoyez le cache.

1. Créez un **[!UICONTROL customer account]** et connectez-vous au front-end.
1. Ajouter un produit avec plus de *2* quantités dans le panier et appliquer un coupon.
1. Cliquez sur **[!UICONTROL Check Out with Multiple Addresses]**.
1. Sélectionnez une adresse distincte pour chaque quantité, passez la commande et effectuez le processus de passage en caisse.
1. Observez le total de la commande auprès de l’administrateur et consultez la remise appliquée.
1. Passez une autre commande avec un autre coupon.
1. Exécutez la variable `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` pour mettre à jour l’utilisation du code de coupon.

<u>Résultats attendus</u>:

Le nombre correct doit s’afficher dans la variable **Durée** et **Utilisé** colonnes avec **Oui** valeur pour **[!UICONTROL manage coupon]** dans le **[!UICONTROL cart price rule]** dans l’administrateur.

<u>Résultats réels</u>:

Le nombre de codes de bon utilisé n’est pas mis à jour dans la variable **Temps utilisé** dans la grille des coupons, et la variable **Utilisé** affiche la colonne *Non* si vous passez une commande avec plusieurs adresses de livraison.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
