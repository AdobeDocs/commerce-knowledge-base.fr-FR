---
title: '[!DNL Admin] - Connexion impossible - taille maximale autorisée de la session dépassée'
description: Résolvez le problème lorsque vous essayez de vous connecter à votre panneau  [!DNL Admin] et que le formulaire s’actualise et que vous ne parvenez pas à vous connecter.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 8718148f6d9a40c9a71484a7fbc818a626e825e1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# [!DNL Admin] - Connexion impossible - taille maximale de session autorisée dépassée

Cet article fournit un correctif pour lorsque vous essayez de vous connecter à votre panneau [!DNL Admin], mais que le formulaire s’actualise et que vous ne pouvez pas vous connecter. En effet, la taille de session [!DNL Admin] a été dépassée.

## Versions affectées

* Adobe Commerce sur site, [toutes les versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problème

Il est impossible de se connecter à [!DNL Admin], car le formulaire continue à se recharger.

## Cause

La taille maximale de session autorisée est dépassée.

## Solution

Recherchez dans le fichier `var/log/support_report.log` des erreurs telles que :

*[2023-07-13T04:26:09.792060+00:00] report.WARNING : la taille de la session de 260572 dépassé la taille maximale autorisée de la session de 256000. [] []
[2023-07-13T04:26:17.056714+00:00] report.WARNING : la taille de la session de 260570 dépassé la taille maximale autorisée de la session de 256000. [][]*

Si ces erreurs s’affichent, la solution serait la suivante :

<u>Adobe Commerce sur site</u> :
1. Augmentez la valeur **[!UICONTROL Max Session Size in Admin]** de la configuration du serveur principal. Pour ce faire, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. Définissez la valeur sur *500000* ou plus. Selon la taille maximale existante signalée dans l’erreur, vous pouvez également définir la valeur sur *0* qui supprimera la taille limite de session.

<u>Adobe Commerce sur l’infrastructure cloud</u> :

(Ce paramètre n’est accessible que dans le [!DNL Admin] lorsque le mode déploiement/opération est par défaut ou développeur. Cependant, seul le mode de déploiement Production est autorisé dans l’environnement cloud.)

Pour augmenter cette valeur, exécutez cette commande dans le terminal (SSH) :

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

Vous pouvez définir une valeur supérieure à *500000* en fonction de la taille maximale existante signalée dans l’erreur et vous pouvez également définir la valeur sur *0* pour supprimer la limite de taille de session.

## Lecture connexe

* [Taille de session](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions) dans le guide des systèmes d’administration.
* [Mode d’opération](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode) dans le Guide de configuration.
* [Connexions sécurisées](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) dans le guide Commerce on Cloud Infrastructure.
