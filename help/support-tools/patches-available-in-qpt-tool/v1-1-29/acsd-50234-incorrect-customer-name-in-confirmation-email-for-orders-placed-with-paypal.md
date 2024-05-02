---
title: 'ACSD-50234 : nom du client incorrect dans l’e-mail de confirmation pour les commandes passées à l’aide de [!DNL PayPal]'
description: Appliquez le correctif ACSD-50234 pour résoudre le problème Adobe Commerce en raison duquel le nom du client s’affiche incorrectement dans l’email de confirmation pour les commandes passées à l’aide de [!DNL PayPal].
exl-id: b2e9c25a-5dd5-4b37-81e3-ca960078da77
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50234 : nom du client incorrect dans l’e-mail de confirmation pour les commandes passées à l’aide de [!DNL PayPal]

Le correctif ACSD-50234 corrige le problème en raison duquel le nom du client s’affiche incorrectement dans l’email de confirmation pour les commandes passées à l’aide de [!DNL PayPal]. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.29 est installée. L’ID de correctif est ACSD-50234. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Courriel de confirmation pour les commandes passées à l’aide de [!DNL PayPal] affiche un nom de client incorrect.

<u>Étapes à reproduire</u>

1. Activer **[!UICONTROL PayPal Express Checkout]**.
1. Accédez au front-end en tant qu’invité.
1. Ajoutez des produits au panier.
1. Passage en caisse à l’aide de **[!UICONTROL PayPal Express Checkout]** comme mode de paiement.
1. Vérifiez l&#39;email de confirmation de commande.

<u>Résultats attendus</u>

L’e-mail de confirmation de commande, l’e-mail de facture et tous les e-mails relatifs à l’envoi sont adressés au nom du client.

<u>Résultats réels</u>

L’e-mail de confirmation de commande, l’e-mail de facture et tous les e-mails relatifs à l’envoi sont adressés à la fonction *Invité*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
