---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.50'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.50.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f62cf4284d7bb99a1ab58df676dfff726c34d327
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.50

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.50.

QPT v1.1.50 comprend les correctifs suivants :

1. **ACSD-59280** : résolution du problème où l’erreur *Appel à une méthode non définie ReflectionUnionType::getName()* se produit lors de l’installation des versions 2.4.4-pX.
1. **ACSD-45049** : résolution du problème en raison duquel le paramètre d’attribut customer *[!UICONTROL Is required]* ne fonctionne pas correctement selon la portée du site web dans Admin.
1. **ACSD-46938** : corrige le problème lié aux performances des déclencheurs de base de données recréés pendant `setup:upgrade`.
1. **ACSD-48210** : résolution du problème de mise à jour de l’attribut *[!UICONTROL website scope]* dans une vue de magasin spécifique remplace les valeurs d’attribut dans la portée globale.
1. **ACSD-54887** : correction du problème en raison duquel le panier du client était effacé une fois la session du client expirée avec *[!UICONTROL Persistent Shopping Cart]* activé.
1. **ACSD-58141** : résolution du problème de régénération de `PHPSESSID` sur les demandes de POST dans la zone de storefront pour un client connecté si [!UICONTROL L2 Redis cache] est activé et que le client est mis à jour à partir de l’administrateur.
1. **ACSD-58352** : résolution du problème en raison duquel les libellés d’attribut de retour pour la vue de magasin par défaut sont renvoyés via l’API GraphQL lorsqu’une vue de magasin autre que la vue par défaut est spécifiée dans l’en-tête de la requête.
1. **ACSD-58442** : correction d’un problème en raison duquel les appareils dont la largeur est de *768px* étaient traités comme mobiles, ce qui entraînait le chargement du menu et de l’en-tête dans une vue mobile plutôt que dans une vue de bureau.
1. **ACSD-58790** : corrige la fonctionnalité de *pincement à zoom* sur les images de page des détails du produit dans la vue mobile sur [!DNL Chrome].
1. **ACSD-59036** : corrige une exception qui se produit lors du chargement de prix de produit avec des limites inférieure et supérieure égales à *$0*.
1. **ACSD-59229** : résolution du problème d’enregistrement des informations relatives aux groupes de clients dans le mauvais segment en raison de l’ancienne valeur de [!UICONTROL X-Magento-Vary] dans la demande.
1. **ACSD-59378** : résolution du problème de mise à jour incorrecte des réécritures d’URL au niveau du magasin lors de l’importation.
1. **ACSD-59514** : résolution du problème en raison duquel les formulaires dans la zone d’administration avec [!DNL Page Builder] lancaient le *[!DNL Page Builder]pendant 5 secondes sans déclencher de verrouillage.* erreur dans la console du navigateur après l’envoi du formulaire et les modifications ne peuvent pas être enregistrées.
1. **ACSD-60303** : correction d’un problème en raison duquel une commande de l’administrateur ne pouvait pas être placée si la minimisation des HTMLS était activée.
1. **ACSD-60441** : résolution du problème de mise à jour des clients via le point de terminaison `V1/customers REST API` lors de l’utilisation du jeton d’accès d’intégration généré à partir du serveur principal.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.

