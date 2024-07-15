---
title: Comment obtenir et appliquer [!UICONTROL security patch]
description: Cet article fournit des instructions sur la manière d’obtenir et d’appliquer un [!UICONTROL security patch] qui a été publié, mais les instructions ne sont pas disponibles.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: b15a1d008b6cc2bdce797768e6ee7029a747e6da
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Comment obtenir et appliquer un [!UICONTROL security patch]

Cet article fournit des instructions sur la manière d’obtenir et d’appliquer un [!UICONTROL security patch] qui a été publié, mais les instructions ne sont pas disponibles.

## Produits et versions concernés

Adobe Commerce On-Premise et Cloud - Toutes les versions

## Cause

La plupart des [!UICONTROL Security Patches] sont publiés sans fichier physique ni correctif à appliquer.

## Solution


### Cas I :

Si un fichier de correctif/correctif physique est mentionné dans les notes de mise à jour :

* Téléchargez le fichier depuis la section de téléchargement de [https://account.magento.com](https://account.magento.com/downloads/view/). (Les utilisateurs d’accès partagé doivent d’abord recevoir des privilèges de téléchargement de la part du propriétaire du compte/titulaire de licence)

**Avertissements :**

Si vous utilisez une ancienne version d’Adobe Commerce et que vous avez acheté l’assistance étendue, votre version doit être l’une des suivantes pour pouvoir appliquer les correctifs de sécurité :

* 2.4.2-p2
* 2.4.3-p3

Si vous ne disposez pas de l’assistance étendue, vous pouvez demander à l’assistance de partager les correctifs avec vous, mais elle ne pourra pas résoudre les problèmes/erreurs que vous pouvez rencontrer lors de leur application.

### Cas II :

Si un fichier de correctif/correctif physique n’est pas mentionné dans les notes de mise à jour :

* **Cloud :**

1. Certains [!UICONTROL Security Patches] peuvent être inclus/publiés dans la dernière version de Cloud Tools Suite (CEE Tools) sous Cloud Patches for Commerce. Consultez les [Notes de mise à jour](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) et si un correctif de sécurité est mentionné dans la version, mettez à niveau le package vers cette version.
1. Si les notes de mise à jour ne mentionnent pas de correctif de sécurité, continuez la lecture.

* **Cloud ou On-Premise :**

* Si aucun fichier de correctif/correctif physique n&#39;est disponible, [mettez à niveau la version Adobe Commerce sur Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X vers la dernière version de correctif 2.4.X-pY.
* Si aucun fichier de correctif/correctif physique n&#39;est disponible, [mettez à niveau la version On-Premise d&#39;Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X vers la dernière version de correctif 2.4.X-pY.

## Lecture connexe

* Voir les [notes de mise à jour de la suite d’outils Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) dans le *Guide de l’infrastructure d’Adobe Commerce on Cloud*.
* Voir [Mise à niveau de la version d’Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) dans le *Guide de l’infrastructure d’Adobe Commerce on Cloud*.
