---
title: 'ACSD-49737 : le coupon est incorrectement marqué comme utilisé après un paiement par carte en échec'
description: Appliquez le correctif ACSD-49737 pour corriger le problème Adobe Commerce en raison duquel le coupon est incorrectement marqué comme utilisé après l’échec du paiement de la carte.
exl-id: 77b5ec9c-3c4c-4da3-ba7e-8be3ccea04d0
feature: Orders, Payments
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737 : Le coupon est incorrectement marqué comme *utilisé* après un échec de paiement par carte

Le correctif ACSD-49737 corrige le problème en raison duquel le coupon est incorrectement marqué comme *utilisé* après un échec du paiement par carte. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 est installé. L’ID de correctif est ACSD-49737. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le coupon est incorrectement marqué comme *utilisé* après un échec de paiement par carte.

<u>Conditions préalables</u> :

1. Configurez la méthode **[!UICONTROL Braintree sandbox payment]**.
1. Assurez-vous que le consommateur [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) est configuré et en cours d’exécution.

<u>Étapes à reproduire</u> :

1. Créez un **[!UICONTROL Cart Price Rule]** avec des codes de bon générés automatiquement.
1. Connectez-vous en tant que client.
1. Ajoutez un ou plusieurs produits au panier.
1. Appliquez un code de bon généré automatiquement.
1. Essayez de passer une commande avec un paiement en échec.
1. Vérifiez l’utilisation des coupons dans l’onglet **[!UICONTROL Cart Price Rule]** sous l’onglet **[!UICONTROL Manage Coupon Codes]** .

<u>Résultats attendus</u> :

Le coupon ne doit pas être marqué comme *utilisé* si le paiement a échoué.

<u>Résultats réels</u> :

* Le code de coupon indique - Utilisé : *Oui*, Temps utilisé : *1*
* Le code coupon est valide pour une utilisation unique uniquement.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Autres étapes requises après l’installation du correctif

(Cette section est facultative ; certaines étapes peuvent être requises après l’application du correctif pour résoudre le problème.) 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
