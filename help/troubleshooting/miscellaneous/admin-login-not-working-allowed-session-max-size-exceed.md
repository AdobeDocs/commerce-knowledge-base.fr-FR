---
title: '[!UICONTROL Admin] connexion ne fonctionne pas - taille maximale de session autorisée dépassée'
description: Résolvez le problème lorsque vous essayez de vous connecter à votre panneau [!UICONTROL Admin] et que le formulaire s’actualise et que vous ne parvenez pas à vous connecter.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: fe4a48581bdfe24da5082b69fb26a8032bd77334
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# [!UICONTROL Admin] connexion ne fonctionne pas - taille maximale de session autorisée dépassée

Cet article fournit un correctif pour le moment où vous essayez de vous connecter à votre panneau [!UICONTROL Admin], mais le formulaire s’actualise et vous ne parvenez pas à vous connecter, ou vous effectuez certaines actions dans le panneau [!UICONTROL Admin] et vous vous déconnectez automatiquement.
Cela est dû au [!UICONTROL Admin] [!UICONTROL Session Size] a été dépassé.

## Versions affectées

* Adobe Commerce On-premise, [toutes les versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problème

Vous présentez l’un des symptômes suivants sur le [!UICONTROL Admin] :

1. Il est impossible de se connecter au [!UICONTROL Admin], car le formulaire ne cesse de se recharger.
1. Vous vous déconnectez automatiquement lorsque vous tentez d’effectuer une action.

## Cause

La taille maximale autorisée pour la session est dépassée.

## Solution

Recherchez des erreurs de ce type dans le fichier `var/log/support_report.log` :

*[2023-07-13T04:26:09.792060+00:00] report.WARNING : la taille de session de 260572 a dépassé la taille maximale autorisée de 256000. [] []
[2023-07-13T04:26:17.056714+00:00] report.WARNING : la taille de session de 260570 a dépassé la taille maximale autorisée de 256000. [][]*

Si ces erreurs s’affichent, la solution serait la suivante :

<u>Adobe Commerce On-premise </u>:
1. Augmentez la valeur **[!UICONTROL Max Session Size in Admin]** à partir de la configuration du serveur principal. Pour ce faire, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. Définissez la valeur sur *500000* ou une valeur supérieure. Selon la taille maximale existante signalée dans l’erreur, vous pouvez également définir la valeur sur *0* ce qui supprimera la limite de taille de session.

<u>Adobe Commerce sur les infrastructures cloud</u> :

(Ce paramètre n’est accessible dans le [!UICONTROL Admin] que lorsque le mode de déploiement/d’opération est *par défaut* ou *développeur*. Cependant, seul le mode de déploiement en production est autorisé dans l’environnement cloud.)

Pour augmenter cette valeur, exécutez cette commande dans le terminal (SSH) :

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

Vous pouvez définir sur supérieur à *500000* en fonction de la taille maximale existante signalée dans l’erreur et vous pouvez également définir la valeur sur *0* pour supprimer la limite de taille de session.

## Lectures connexes

* [Taille de la session](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions) dans le guide des systèmes d’administration
* [Mode de fonctionnement](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode) dans le Guide de configuration
* [Connexions sécurisées](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) dans le Guide de Commerce sur les infrastructures cloud
