---
title: Les anciens membres de l’équipe reçoivent des e-mails de notification Adobe Commerce Cloud
description: Cet article fournit une solution à Adobe Commerce sur les e-mails de notification d’infrastructure cloud envoyés aux anciens membres de l’équipe.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: bd199fac6d8f33491b9fa0f508b2bb52d56b46a5
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Les anciens membres de l’équipe reçoivent des e-mails de notification Adobe Commerce Cloud

Cet article fournit une solution pour supprimer de la liste des destinataires des e-mails de notification les utilisateurs qui sont :

* Anciens membres de l’équipe qui ne sont plus associés à votre projet.
* Membres actuels de l’équipe qui ne devraient pas recevoir les notifications.

## Problème

Un avis de panne détectée ou de problème important concernant le projet/l’environnement cloud a été envoyé à votre équipe. Cela inclut les membres qui peuvent ne plus être associés à votre projet, tels que les développeurs externes/agences ou les intégrateurs système. Vous souhaitez que ces utilisateurs cessent de recevoir des notifications.

## Solution

>[!NOTE]
>
>Si vous êtes un développeur externe/une agence ou un intégrateur système et que vous n’êtes plus associé au projet, vous devez contacter le propriétaire du projet ou l’administrateur du projet pour obtenir de l’aide.

Il existe deux manières d’arrêter les notifications en supprimant le(s) utilisateur(s) de votre projet :

* Méthode 1 : utilisation de l’[!DNL Project URL] cloud. Pour connaître la procédure à suivre, voir [Gérer l’accès des utilisateurs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr) dans le guide Commerce sur les infrastructures cloud.
* Méthode 2 : utiliser le [!DNL CLI] magento-cloud. Pour connaître la procédure à suivre, consultez la section [Gérer les utilisateurs avec le [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr#manage-users-with-the-cli) dans le guide Commerce sur les infrastructures cloud.

Si cela a déjà été fait et que les notifications par e-mail continuent d’inclure ces utilisateurs, envoyez un ticket d’assistance pour demander qu’ils soient supprimés du paramètre *[!UICONTROL Always CC]* sur le compte.

## Lecture connexe

* [Afficher le rôle de projet d’un utilisateur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr#view-a-user&?lang=fr#39;s-project-role) dans le guide Commerce sur les infrastructures cloud .
* [Comment inclure un membre de l’équipe dans les notifications d’assistance &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html?lang=fr) dans la base de connaissances de Commerce.
