---
title: Impossible d’accéder à l’interface utilisateur d’Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit des solutions au problème en raison duquel vous ne pouvez pas vous connecter à l’interface utilisateur d’Adobe Commerce sur une infrastructure cloud et obtenir l’erreur « 403 ».
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%
---
# Impossible d’accéder à l’interface utilisateur d’Adobe Commerce sur l’infrastructure cloud

Cet article fournit des solutions au problème où vous ne pouvez pas vous connecter à l’interface utilisateur de votre Adobe Commerce sur une infrastructure cloud et obtenir l’erreur *403*.

## Problème

Lors de la première tentative de connexion à l’interface utilisateur de votre Adobe Commerce sur l’infrastructure cloud, vous obtenez une erreur *403 : Accès à l’environnement refusé*. Cette erreur peut se produire, car accéder à l’URL du cloud pour la première fois charge la branche principale et vous n’avez peut-être pas accès à cette branche.

## Solution

Si vous obtenez une erreur 403 lors de l’accès initial à l’URL, assurez-vous de disposer d’un rôle dans la branche principale.

1. Contactez le propriétaire de la licence ou un super utilisateur du projet et assurez-vous qu’il vous a fourni l’accès en tant qu’**utilisateur au niveau de l’environnement**, également décrit dans [Projets cloud > Gérer les utilisateurs à partir de la console cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-cloud-console) dans notre documentation destinée aux développeurs.

   Si vous disposez uniquement d’un rôle applicable dans une branche spécifique, vous devez accéder à l’URL de cette branche, par exemple, .
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   La prochaine fois que vous accéderez à l’URL principale, elle apparaîtra par défaut sur le dernier environnement que vous avez visité.

1. Si vous ne parvenez toujours pas à vous connecter, сcontactez le propriétaire de la licence ou un super utilisateur pour le projet et assurez-vous qu’il vous a fourni l’accès en tant qu’**utilisateur au niveau du projet**, comme décrit dans [Projets cloud > Ajouter un utilisateur au projet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-a-user-to-the-project) dans notre documentation destinée aux développeurs.
1. Si l’erreur persiste, [envoyez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).
