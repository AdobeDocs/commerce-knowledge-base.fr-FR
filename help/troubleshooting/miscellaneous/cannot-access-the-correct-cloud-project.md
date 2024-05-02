---
title: Impossible d’accéder au compte/projet Adobe Commerce correct ou le projet est absent de votre compte
description: Cet article fournit un correctif pour le problème lorsque vous ne pouvez pas accéder au projet Adobe Commerce cloud approprié en cas de modification des propriétés ou des modifications des adresses électroniques.
exl-id: 165b9a18-6e84-4f0f-b377-a07152d55c9e
hide: true
hidefromtoc: true
feature: Cloud, Paas
role: Developer
source-git-commit: 423a392eb32df69c38b84081ac2ed17ae1efdc7b
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Impossible d’accéder au bon compte/projet cloud ou le projet est absent de votre compte

Cet article fournit un correctif pour les problèmes suivants après qu’une modification a été apportée à la propriété du compte ou aux adresses électroniques associées :

1. Vous ne pouvez pas accéder aux projets Adobe Commerce cloud corrects.
1. Aucun projet Adobe Commerce cloud n’est affiché sous votre compte à l’adresse [accounts.magento.cloud/user](https://accounts.magento.cloud/user).
1. Vous voyez les détails d’un autre compte (c.-à-d. le propriétaire précédent du compte) à l’adresse [accounts.magento.cloud/user](https://accounts.magento.cloud/user).

## Problème

Vous ne pouvez pas accéder au projet Adobe Commerce cloud approprié en cas de modification des propriétés ou des adresses électroniques.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Cause

Ce problème survient généralement lorsque l’authentification unique (SSO) du propriétaire précédent du projet est toujours intégrée à Adobe.com après :

1. La propriété du projet cloud vous a été transférée (l’utilisateur) et vous voyez le compte du propriétaire du projet d’origine. Cliquez ici pour [solution](#solution-for-cause-one-and-two).

   OU

1. Vous (l’utilisateur) avez déménagé dans une autre société, accompagnée d’un changement de l’adresse électronique et des projets auxquels vous avez accès. Vous voyez les projets auxquels vous aviez accès dans votre rôle/société précédent. Cliquez ici pour [solution](#solution-for-cause-one-and-two).

   OU

1. Vous avez remplacé votre adresse électronique à l’adresse https://account.adobe.com par une autre adresse électronique qui n’est actuellement pas associée à un projet cloud. Cliquez ici pour [solution](#solution-for-cause-three).

## Solution pour la première et la deuxième cause {#solution-for-cause-one-and-two}

La solution pour lorsque le problème est provoqué par un et deux est de déconnecter l’intégration de l’authentification unique à Adobe.com. Pour vous déconnecter, procédez comme suit :

1. À partir de https://accounts.magento.cloud/user, développez la **[!UICONTROL Single Sign-On]** . Cliquez sur **[!UICONTROL Disconnect from Adobe.com]**, pour vous déconnecter.

   ![authentification unique sur adobe-connect](assets/sso-adobe-disconnect.png)

1. Cliquez sur **[!UICONTROL Disconnect]**.

   ![adobe-disconnect](assets/adobe-disconnect.png)

1. Déconnectez-vous.
1. Cliquez sur le bouton **[!UICONTROL Adobe.com]** bouton .

   ![Magento.com](assets/adobe-welcome-login.png)

1. Vous devriez maintenant pouvoir voir le compte correct et accéder au projet cloud approprié.

## Solution pour la troisième cause {#solution-for-cause-three}

Si le problème a été causé par la troisième cause, demandez à un super-utilisateur existant sur le projet d’ajouter votre nouvelle adresse électronique au projet. Pour plus d’informations, voir [Gestion de l’accès des utilisateurs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).
