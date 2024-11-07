---
title: 'ACSD-44591 : erreurs de commande sans confirmation CAPTCHA'
description: Le correctif ACSD-44591 résout le problème où l’utilisateur rencontre des erreurs lorsqu’il tente de passer une commande sans confirmation CAPTCHA.
exl-id: 5459aa14-dcba-474d-aafa-e4cc73daafbc
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-44591 : erreurs de commande sans confirmation CAPTCHA

Le correctif ACSD-44591 résout le problème où l’utilisateur rencontre des erreurs lorsqu’il tente de passer une commande sans confirmation CAPTCHA.
Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 est installé. L’ID de correctif est ACSD-44591. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur obtient des erreurs lorsqu’il tente de passer une commande sans confirmation CAPTCHA.

<u>Étapes à reproduire</u> :

1. Configurez le Google ReCaptcha v2 (je ne suis pas un robot).
1. Activez ReCaptcha pour le paiement.
1. Essayez de passer une commande sans cliquer sur le ReCaptcha.
1. Une fois que vous avez reçu le message d&#39;erreur pour ReCaptcha manquant (*Échec de la validation ReCaptcha, veuillez réessayer*), cliquez sur **ReCaptcha** et essayez de passer une commande.

<u>Résultats attendus</u> :

La commande ne sera pas placée avec un ReCaptcha incorrect.

<u>Résultats réels</u> :

Vous obtenez les erreurs suivantes :

* *Échec de la validation ReCaptcha, veuillez réessayer*
* *Aucun panier avec id = 1*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
