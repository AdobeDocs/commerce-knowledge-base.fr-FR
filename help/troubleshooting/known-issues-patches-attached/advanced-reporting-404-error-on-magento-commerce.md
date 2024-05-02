---
title: '[!DNL Advanced Reporting] Erreur 404 sur Adobe Commerce'
description: Cet article fournit un correctif pour le problème Adobe Commerce lorsqu’un commerçant reçoit une erreur 404 lorsqu’il tente d’accéder à [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Une fois ce correctif installé, les utilisateurs pourront accéder à [!DNL Advanced Reporting].
exl-id: bac61704-44fe-4bd2-b342-af90219231ef
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# [!DNL Advanced Reporting] Erreur 404 sur Adobe Commerce

Cet article fournit un correctif pour le problème Adobe Commerce lorsqu’un commerçant reçoit une erreur 404 lorsqu’il tente d’accéder à [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Une fois ce correctif installé, les utilisateurs pourront accéder à [!DNL Advanced Reporting].

Pour vérifier si ce correctif peut résoudre ce problème, consultez d’abord les journaux à l’aide de la commande suivante :

`zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz`

Si vous voyez le `Not valid cipher` , appliquez le correctif joint.

## Produits et versions concernés

Adobe Commerce 2.2.6

## Problème

Un commerçant reçoit une erreur 404 lorsqu’il tente d’accéder à [!DNL Advanced Reporting].

## Solution

Pour résoudre le problème, appliquez le correctif joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant : [Télécharger MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
