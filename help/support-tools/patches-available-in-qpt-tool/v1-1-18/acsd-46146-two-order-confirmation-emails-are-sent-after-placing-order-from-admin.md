---
title: 'ACSD-46146 : deux emails de confirmation de commande envoyés après le placement de la commande de l’administrateur'
description: Le correctif ACSD-46146 résout le problème d’envoi de deux emails de confirmation de commande après le placement d’une commande de la part de l’administrateur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 est installé. L’ID de correctif est ACSD-46146. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: 3bf2cccf-7a40-48ca-ab51-ffb5939f8802
feature: Admin Workspace, Communications, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-46146 : deux emails de confirmation de commande envoyés après le placement de la commande depuis l’administrateur

Le correctif ACSD-46146 résout le problème d’envoi de deux emails de confirmation de commande après le placement d’une commande de la part de l’administrateur. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.18 est installé. L’ID de correctif est ACSD-46146. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Deux emails de confirmation de commande sont envoyés après avoir passé une commande de l’administrateur.

<u>Étapes à reproduire</u> :

1. Ouvrez l’administrateur Commerce > **Ventes** > **Commandes** > **Créer une commande**.
1. Passez une commande avec les paramètres de paiement par défaut (chèque/mandat) et d&#39;expédition (taux forfaitaire).

<u>Résultats attendus</u> :

Un seul email de confirmation de commande est envoyé.

<u>Résultats réels</u> :

Deux emails de confirmation de commande sont envoyés après avoir passé une commande de l’administrateur.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
