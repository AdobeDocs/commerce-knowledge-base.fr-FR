---
title: Comment obtenir et appliquer des [!UICONTROL security patch]
description: Cet article fournit des instructions sur la manière d’obtenir et d’appliquer une [!UICONTROL security patch] qui a été publiée, mais les instructions ne sont pas disponibles.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: 3c7234b52e5e4465d95c95345e1c070c28600dfb
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Comment obtenir et appliquer un [!UICONTROL security patch]

>[!NOTE]
>Si vous disposez d’une installation On-Premise et que vous n’utilisez pas de systèmes de contrôle de version tels que [!DNL CVS] ou [!DNL GitHub] pour gérer votre code, votre hôte web peut vous aider à appliquer le correctif. N’hésitez pas à les contacter pour obtenir de l’aide.

Cet article fournit des instructions sur la manière d’obtenir et d’appliquer une [!UICONTROL security patch] qui a été publiée, mais les instructions ne sont pas disponibles.

## Produits et versions concernés

Adobe Commerce On-Premise et Cloud - Toutes les versions


## Cause

La plupart des [!UICONTROL Security Patches] sont publiés sans correctif ou correctif isolé à appliquer et nécessiteront une mise à niveau vers la version [!UICONTROL Security Patch].

## Solution


### Cas I :

* Si un fichier de correctif ou un correctif logiciel isolé est mentionné dans les [notes de mise à jour](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite) téléchargez le fichier à partir de la section de téléchargement de [https://account.magento.com](https://account.magento.com/downloads/view/). Les utilisateurs d’accès partagé doivent d’abord recevoir des privilèges de téléchargement de la part du propriétaire du compte ou du titulaire de licence.

**Avertissements:**

Si vous utilisez une ancienne version d’Adobe Commerce (2.4.4), vous aurez automatiquement reçu la prise en charge étendue. Votre version doit être l&#39;une des versions non prises en charge suivantes pour pouvoir appliquer les derniers correctifs de sécurité disponibles :

2.4.4 - 2.4.4-p11

Les versions non prises en charge (2.3.x, 2.4.0 à 2.4.3) ne sont pas éligibles à la prise en charge. Vous devez d’abord effectuer une mise à niveau vers une version prise en charge pour tirer parti des derniers correctifs de sécurité.

Si vous ne disposez pas de la prise en charge étendue, vous pouvez demander à l’assistance de partager les correctifs avec vous, mais ils ne pourront pas résoudre les problèmes/erreurs que vous pourriez rencontrer lors de leur application.

### Cas II :

Les correctifs isolés ne sont fournis que dans des cas exceptionnels, et il ne s’agit pas de la forme préférée pour implémenter des correctifs de sécurité.

Si un fichier de correctif/correctif isolé n’est pas mentionné dans les notes de mise à jour :

* **Cloud:**

1. Certaines [!UICONTROL Security Patches] peuvent être incluses/publiées dans la dernière version de Cloud Tools Suite (outils ECE) sous Cloud Patches pour Commerce. Vérifiez les [notes de mise à jour](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) et si un correctif de sécurité est mentionné dans la version, mettez à niveau le package vers cette version.
1. Si les notes de mise à jour ne mentionnent pas de correctif de sécurité, poursuivez la lecture.

* **Cloud ou On-Premise:**

* Si aucun fichier de correctif ou correctif logiciel isolé n’est disponible, [mettez à niveau la version d’Adobe Commerce sur Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X vers la dernière version de correctif 2.4.X-pY.
* Si aucun fichier de correctif ou correctif logiciel isolé n&#39;est disponible, [mettez à niveau la version On-Premise d&#39;Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X vers la dernière version de correctif 2.4.X-pY.

## Lecture connexe

* Voir [Notes de mise à jour de la suite d’outils Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) dans le *Guide d’Adobe Commerce sur les infrastructures cloud*.
* Voir [Mise à niveau de la version d’Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) dans le *Guide d’Adobe Commerce sur les infrastructures cloud*.
