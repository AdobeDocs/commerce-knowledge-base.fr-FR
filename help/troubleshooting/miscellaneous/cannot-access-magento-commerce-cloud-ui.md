---
title: Impossible d’accéder à Adobe Commerce dans l’interface utilisateur de l’infrastructure cloud
description: Cet article fournit des solutions pour le problème où vous ne pouvez pas vous connecter à votre Adobe Commerce sur l’interface utilisateur de l’infrastructure cloud et obtenir l’"erreur 403".
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
source-git-commit: 3d3d2da45d164efbbbaf8c878967caf83f845a59
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Impossible d’accéder à Adobe Commerce dans l’interface utilisateur de l’infrastructure cloud

Cet article fournit des solutions pour le problème où vous ne pouvez pas vous connecter à votre Adobe Commerce sur l’interface utilisateur de l’infrastructure cloud et obtenir l’ *403 error*.

## Problème

Lors de la première tentative de connexion à votre Adobe Commerce sur l’interface utilisateur de l’infrastructure cloud, vous obtenez une erreur *403 : Accès à l’environnement refusé*. Cette erreur peut se produire, car l’accès à l’URL du cloud pour la première fois charge la branche principale et vous n’avez peut-être pas accès à cette branche.

## Solution

Si vous obtenez une erreur 403 lors de l’accès à l’URL pour la première fois, assurez-vous que vous avez un rôle dans la branche principale.

1. С contactez le propriétaire de la licence ou un super-utilisateur sur le projet et assurez-vous qu’il vous a donné accès en tant qu’ **utilisateur de niveau environnement**, également décrit dans [Projets cloud > Gérer les utilisateurs à partir de la console cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr#manage-users-from-the-cloud-console) dans notre documentation destinée aux développeurs.

   Si vous ne disposez que d’un rôle applicable dans une branche spécifique, vous devez accéder à l’URL de cette branche, par exemple :
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   La prochaine fois que vous accéderez à l’URL principale, elle sera utilisée par défaut dans le dernier environnement que vous avez visité.

1. Si vous ne parvenez toujours pas à vous connecter, с contactez le propriétaire de la licence ou un super-utilisateur sur le projet et assurez-vous qu’il vous a donné accès en tant qu’ **utilisateur au niveau du projet**, comme décrit dans [Projets cloud > Ajouter un utilisateur au projet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr#add-a-user-to-the-project) dans la documentation destinée aux développeurs.
1. Si l’erreur persiste, [soumettez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
