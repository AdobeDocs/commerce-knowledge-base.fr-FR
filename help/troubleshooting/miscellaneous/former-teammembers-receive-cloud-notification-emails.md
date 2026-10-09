---
title: Les anciens membres de l’équipe reçoivent des e-mails de notification Adobe Commerce Cloud
description: Cet article fournit une solution à Adobe Commerce sur les e-mails de notification d’infrastructure cloud envoyés aux anciens membres de l’équipe.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '336'
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

* [Afficher le rôle de projet d’un utilisateur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr#view-a-user's-project-role) dans le guide Commerce sur les infrastructures cloud .
* [Comment inclure un membre de l’équipe dans les notifications d’assistance &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html?lang=fr) dans la base de connaissances de Commerce.
