---
title: "MBI : réauthentification des intégrations"
description: Cet article fournit des solutions pour réautoriser une intégration afin d’accorder à Magento Business Intelligence (MBI) les privilèges requis pour extraire des données d’un service tiers. Une réautorisation est requise lorsque ces privilèges sont révoqués.
exl-id: c608d6f9-64a5-44f8-9d7b-9a85a2668775
feature: Commerce Intelligence, Integration
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# MBI : réauthentification des intégrations

Cet article fournit des solutions pour réautoriser une intégration afin d’accorder à Magento Business Intelligence (MBI) les privilèges requis pour extraire des données d’un service tiers. Une réautorisation est requise lorsque ces privilèges sont révoqués.

## Intégrations base de données et SaaS

Pour obtenir la liste des intégrations Base de données et SaaS, reportez-vous à la section [Connexion aux données externes à l’aide d’une intégration](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/analyze/saas/integrations) dans notre documentation destinée aux développeurs. (Lors de l’ouverture de la page, utilisez la table des matières sur la gauche pour la navigation).

## Vous rencontrez des problèmes de connexion ?

L’autorisation d’une intégration accorde à MBI les privilèges requis pour extraire des données d’un service tiers. Une réautorisation est requise lorsque ces privilèges sont révoqués.

Cela peut se produire pour plusieurs raisons :

* un problème avec le service tiers ;
* expiration du jeton d’authentification
* une modification apportée à votre compte d’administrateur ;
* ou un problème interne dans l&#39;IMS

L’état de toutes les intégrations se trouve sur la page Intégrations ( **Gérer les données > Intégrations** ) :

![Intégrations_page.png](assets/Integrations_page.png)

Pour vous reconnecter, vous devrez peut-être saisir à nouveau les informations d’identification de votre compte. Dans certains cas, vous devrez peut-être générer de nouvelles clés d’API pour l’intégration du problème. Cliquez sur le nom de l’intégration du problème pour lancer le processus de réautorisation.

Si le problème persiste, [soumettez un ticket d&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
