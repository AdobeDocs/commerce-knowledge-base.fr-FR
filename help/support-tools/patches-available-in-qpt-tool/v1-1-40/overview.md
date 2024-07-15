---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.40'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.40.
feature: Tools and External Services
role: Admin, Developer
exl-id: 10387151-a3e2-4cf3-8194-d1be859cf29e
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.40

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.40.

QPT v1.1.40 comprend les correctifs suivants :

1. **ACSD-54680** : corrige le problème lorsqu’il n’est pas possible de traiter une citation B2B envoyée pour un produit avec plusieurs sources affectées.
1. **ACSD-54040** : correction d’un problème en raison duquel le champ *[!UICONTROL Created]* n’était pas renseigné dans l’ordre lorsque les modules B2B étaient activés.
1. **ACSD-54319** : correction d’un problème en raison duquel le prix du produit affichait zéro dans le rapport *[!UICONTROL Product in Cart]*.
1. **ACSD-53378** : améliore le temps de chargement de la page de passage en caisse pour les clients qui disposent de carnets d’adresses volumineux.
1. **ACSD-52657** : résolution du problème en raison duquel le minicart n’est pas mis à jour dans l’aperçu de magasin secondaire, qui utilise un sous-domaine.
1. **ACSD-53414** : correction d’un problème en raison duquel un utilisateur administrateur restreint pouvait voir des pages CMS en dehors de leur portée d’autorisation.
1. **ACSD-54472** : résolution du problème en raison duquel les clients d’une société rejetée peuvent toujours s’authentifier et les clients d’une société bloquée et rejetée peuvent toujours passer des commandes. Le correctif ajoute une validation supplémentaire pour les points de terminaison GraphQL.
1. **ACSD-52801** : ajoute l’option permettant d’effectuer une correspondance partielle lors de la recherche de produits dans GraphQL.
1. **ACSD-55004** : résolution du problème de blocage du programme de validation lors du téléchargement d’un fichier d’importation supérieur à la valeur configurée dans `php.ini`.
1. **ACSD-54989** : résolution du problème de l’impossibilité pour un administrateur de la société de passer une commande lorsque *[!UICONTROL Enable Purchase Orders]* est défini sur *[!UICONTROL Yes]* et *[!UICONTROL Purchase Order]* sur *[!UICONTROL No]*.
1. **ACSD-54007** : corrige l’erreur *&quot;Undefined array key &quot;_scope&quot;* lors de l’importation de données client.
1. **ACSD-55031** : corrige l’erreur *Type &quot;mixte&quot; ne peut pas être nul* lors de la compilation.
1. **ACSD-54961** : correction d’un problème en raison duquel un utilisateur administrateur restreint ne pouvait pas mettre à jour en masse l’état *Product Review*.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
