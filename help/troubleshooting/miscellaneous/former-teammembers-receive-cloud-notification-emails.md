---
title: Les anciens membres de l’équipe reçoivent des e-mails de notification cloud Adobe Commerce
description: Cet article fournit une solution à Adobe Commerce concernant l’envoi d’emails de notification d’infrastructure cloud aux anciens membres de l’équipe.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: 0017d43e221ef3023630f714c34aa65b368e214f
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Les anciens membres de l’équipe reçoivent des e-mails de notification cloud Adobe Commerce

Cet article fournit une solution pour supprimer de la liste des destinataires les adresses email de notification qui sont :
* Anciens membres de l’équipe qui ne sont plus associés à votre projet.
* Les membres actuels de l’équipe qui ne doivent pas recevoir les notifications.

## Problème

Un avis d’interruption détectée ou d’un problème important concernant le projet/l’environnement cloud a été envoyé à votre équipe. Cela inclut les membres qui peuvent ne plus être associés à votre projet, tels que les développeurs externes/d’agence ou les intégrateurs système. Vous souhaitez que ces utilisateurs cessent de recevoir des notifications.

## Solution

Il existe deux façons d’arrêter les notifications en supprimant le ou les utilisateurs de votre projet :

* Méthode 1 : utilisation du cloud [!DNL Project URL]. Pour connaître les étapes, reportez-vous à la section [Gestion de l’accès des utilisateurs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) du guide Commerce on cloud infrastructure.
* Méthode 2 : utilisation du cloud magento [!DNL CLI]. Pour connaître les étapes, reportez-vous à la section [Gestion des utilisateurs avec le  [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli) du guide Commerce on cloud infrastructure.

Si cela a déjà été fait et que les notifications par e-mail continuent d’inclure ces utilisateurs, envoyez un ticket d’assistance pour demander qu’ils soient supprimés du paramètre *[!UICONTROL Always CC]* du compte.

## Lecture connexe

* [Affichez le rôle de projet d’un utilisateur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user’s-project-role) dans le guide Commerce on cloud infrastructure.
* [Comment inclure un membre de l’équipe dans les notifications d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html) dans la base de connaissances Commerce.
