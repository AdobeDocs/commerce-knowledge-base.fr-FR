---
title: "ACSD-57588 : Erreur dans le traitement des identifiants de région lors de l’expédition vers plusieurs adresses"
description: Appliquez le correctif ACSD-57588 pour résoudre le problème Adobe Commerce en raison duquel l’envoi d’une commande à plusieurs adresses déclenche une erreur lors du traitement des identifiants de région.
feature: Orders, Shipping/Delivery
role: Admin, Developer
source-git-commit: 1899e4601d292a8543d1c34e622251a7f6aed124
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-57588 : Erreur dans le traitement des identifiants de région lors de l&#39;expédition vers plusieurs adresses

Le correctif ACSD-57588 corrige le problème en raison duquel l’envoi d’une commande à plusieurs adresses déclenche une erreur lors du traitement des ID de région. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 est installé. L’ID de correctif est ACSD-57588. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Erreur déclenchée lors du traitement des identifiants de région lors de l’expédition vers plusieurs adresses.

<u>Étapes à reproduire</u> :

1. Configurez le mode de paiement [!DNL Braintree].
1. Connectez-vous en tant que client sur le storefront.
1. Ajoutez un produit au panier, puis affichez et modifiez le panier.
1. Ajoutez plusieurs adresses *(par exemple, Royaume-Uni, États-Unis, CA)* pendant le processus de passage en caisse et passez en revue la commande.
1. Sur la page de paiement, sélectionnez l’option de paiement par carte de crédit, saisissez les informations d’identification nécessaires et passez la commande.

<u>Résultats attendus</u> :

La commande peut être passée avec succès.

<u>Résultats réels</u> :

La commande n’est pas placée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
