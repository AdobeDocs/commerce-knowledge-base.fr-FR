---
title: Impossible d’accéder à l’interface utilisateur d’Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit des solutions au problème en raison duquel vous ne pouvez pas vous connecter à l’interface utilisateur d’Adobe Commerce sur une infrastructure cloud et obtenir l’erreur « 403 ».
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Impossible d’accéder à l’interface utilisateur d’Adobe Commerce sur l’infrastructure cloud

Cet article fournit des solutions au problème où vous ne pouvez pas vous connecter à l’interface utilisateur de votre Adobe Commerce sur une infrastructure cloud et obtenir l’erreur *403*.

## Problème

Lors de la première tentative de connexion à l’interface utilisateur de votre Adobe Commerce sur l’infrastructure cloud, vous obtenez une erreur *403 : Accès à l’environnement refusé*. Cette erreur peut se produire, car accéder à l’URL du cloud pour la première fois charge la branche principale et vous n’avez peut-être pas accès à cette branche.

## Solution

Si vous obtenez une erreur 403 lors de l’accès initial à l’URL, assurez-vous de disposer d’un rôle dans la branche principale.

1. Contactez le propriétaire de la licence ou un super utilisateur du projet et assurez-vous qu’il vous a fourni l’accès en tant qu’**utilisateur au niveau de l’environnement**, également décrit dans [Projets cloud > Gérer les utilisateurs à partir de la console cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr#manage-users-from-the-cloud-console) dans notre documentation destinée aux développeurs.

   Si vous disposez uniquement d’un rôle applicable dans une branche spécifique, vous devez accéder à l’URL de cette branche, par exemple, .
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   La prochaine fois que vous accéderez à l’URL principale, elle apparaîtra par défaut sur le dernier environnement que vous avez visité.

1. Si vous ne parvenez toujours pas à vous connecter, сcontactez le propriétaire de la licence ou un super utilisateur pour le projet et assurez-vous qu’il vous a fourni l’accès en tant qu’**utilisateur au niveau du projet**, comme décrit dans [Projets cloud > Ajouter un utilisateur au projet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr#add-a-user-to-the-project) dans notre documentation destinée aux développeurs.
1. Si l’erreur persiste, [envoyez un ticket d’assistance](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).
