---
title: Migration de l’intégration de la méthode d’expédition '[!DNL UPS] de [!DNL SOAP] vers [!DNL RESTful API]'
promoted: true
description: Appliquez un correctif pour gérer la migration de l’intégration de la méthode de livraison  [!DNL UPS]  de [!DNL SOAP] vers [!DNL RESTful API] pour Adobe Commerce 2.4.4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL UPS] Migration de l’intégration des méthodes de livraison de [!DNL SOAP] à [!DNL RESTful API]

>[!NOTE]
>
>Si vous avez téléchargé l’un des trois correctifs de cet article avant le **6 juin 2024** : si vous rencontrez ce problème en raison des mesures [!DNL Metric System/SI] (kilogrammes et centimètres) non utilisées, vous devez réappliquer l’un de ces nouveaux correctifs mis à jour publiés dans cet article pour votre version 2.4.4+/2.4.5+/2.4.6+ de Adobe Commerce. de nouveau, car sinon vous ne pourrez pas sélectionner les [!DNL Metric System/SI] mesures de **kilogrammes** et de **centimètres** dans les méthodes d’expédition [!DNL UPS] de **[!DNL Admin configuration]**. Ces nouveaux correctifs sont compatibles avec les correctifs publiés précédemment. Ce problème sera corrigé définitivement dans le cadre de la prochaine version d’Adobe Commerce 2.4.7-p1 prévue pour le **11 juin 2024**.

>[!NOTE]
>
>Si vous avez téléchargé l’un des trois correctifs de cet article avant le **10 octobre 2023**, vous devez réappliquer l’un de ces correctifs publiés dans cet article pour votre version 2.4.4+/2.4.5+/2.4.6+ d’Adobe Commerce/Magento Open Source, car vous ne pourrez pas sélectionner et configurer des méthodes d’expédition spécifiques [!DNL UPS] dans le **[!DNL Admin configuration]** et vous devrez tous les activer. Ces nouveaux correctifs sont compatibles avec les correctifs publiés précédemment.

Cet article fournit un correctif pour résoudre les problèmes liés à la migration de l’intégration de la méthode de livraison [!DNL United Parcel Service (UPS)] de [!DNL SOAP] à [!DNL RESTful API] pour Adobe Commerce 2.4.4 - 2.4.6-pX.

Selon les dernières mises à jour du modèle de sécurité [!DNL UPS API], [!DNL UPS] a mis en oeuvre un modèle de sécurité [!DNL OAuth 2.0] pour tous les [!DNL APIs] (plus de détails disponibles dans le [[!DNL UPS] Guide de migration des clés d’accès au portail du développeur](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)) afin d’améliorer la sécurité globale afin de réduire la fraude et de fournir des fonctionnalités [!DNL API] améliorées.

Cette modification a un impact sur l’implémentation actuelle de l’intégration des méthodes de livraison [!DNL UPS] dans Adobe Commerce et nécessite que nous corrigions notre implémentation actuelle et que nous migrions de [!DNL SOAP API] vers [!DNL RESTful API] pour pouvoir prendre en charge les protocoles d’authentification [!DNL OAuth 2.0].

**À compter de juin 2024**, les marchands Adobe Commerce ne pourront pas traiter avec notre intégration [!DNL UPS] actuelle. Nous publions donc ce correctif qui permet à Adobe Commerce 2.4.4+/2.4.5+/2.4.6.6+ de migrer vers le dernier [!DNL UPS REST APIs].

Ce problème sera corrigé dans Adobe Commerce/Magento Open Source version 2.4.7 et le correctif sera également inclus dans la version 2.4.7-beta2 d’octobre 2023.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud et sur site, et Magento Open Source :

* 2.4.4
* 2.4.4-pX
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6-pX

## Causes

Le [!DNL UPS] a publié une [mise à jour de sécurité pour son [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

Si vous avez une origine européenne (d’autres origines peuvent rencontrer le même problème) que l’origine de l’envoi, cela provoquera une erreur dans la requête [!DNL UPS REST] :
&quot;*Une expédition ne peut pas avoir un KGS/IN ou LBS/CM ou OZS/CM comme unité de mesure.*&quot;

## Solution

Utilisez les correctifs ci-joint suivants, en fonction de votre version d’Adobe Commerce/de Magento Open Source :

Pour résoudre le problème dans les versions 2.4.4+, 2.4.5+ et 2.4.6+, vous devez appliquer le correctif correspondant à votre version d’Adobe Commerce/Magento Open Source ci-dessous.

## Correctif

Utilisez les correctifs ci-joint suivants, en fonction de votre version d’Adobe Commerce/de Magento Open Source :

### Pour les versions 2.4.4, 2.4.4-pX :

* [AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### Pour les versions 2.4.5, 2.4.5-pX :

* [AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### Pour les versions 2.4.6, 2.4.6-pX :

* [AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

## Comment appliquer le correctif

Décompressez le fichier et reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) dans notre base de connaissances de support pour obtenir des instructions.

## Comment déterminer si les correctifs ont été appliqués

Étant donné qu’il n’est pas possible de vérifier facilement si le problème a été corrigé, vous pouvez vérifier si le correctif a bien été appliqué. Cela utilise (exemple : *AC-9363*) comme correctif à vérifier.

<u>Pour ce faire, procédez comme suit</u> :

1. [Installez le  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Exécutez la commande :

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Vous devriez voir une sortie similaire à celle-ci, où AC-9363 renvoie l’état *Appliqué* :

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
