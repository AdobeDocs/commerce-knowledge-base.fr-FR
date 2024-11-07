---
title: "MDVA-36021 : les utilisateurs reçoivent un message d’erreur lors de l’ouverture des détails de la commande"
description: Le correctif MDVA-36021 résout le problème où les utilisateurs reçoivent le message d’erreur *Call to a member function getId()* lors de la tentative d’ouverture des détails de la commande. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 est installé. L’ID de correctif est MDVA-36021. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 73b1f3c6-5dc4-48e4-8f3f-681be84f7638
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-36021 : les utilisateurs reçoivent un message d’erreur lors de l’ouverture des détails de la commande

Le correctif MDVA-36021 résout le problème où les utilisateurs reçoivent le message d’erreur *Call to a member function getId()* lors de la tentative d’ouverture des détails de la commande. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 est installé. L’ID de correctif est MDVA-36021. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.4.1, 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque les utilisateurs tentent d’ouvrir les détails de la commande, le message d’erreur suivant s’affiche sur la page des détails de la commande dans l’Admin : *report.CRITICAL: Error: Call to a member function getId() on array in /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*.

<u>Conditions préalables</u> :

Le système doit avoir des paramètres fiscaux et des commandes avec des taux d&#39;imposition spécifiques.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur Commerce.
1. Accédez à **Sales** > **Commandes** > **Open Order**.

<u>Résultats attendus</u> :

La commande est ouverte sans erreur.

<u>Résultats réels</u> :

Vous obtenez un message d’erreur similaire à ce qui suit : *report.CRITICAL: Error: Call to a member function getId() on array in /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
