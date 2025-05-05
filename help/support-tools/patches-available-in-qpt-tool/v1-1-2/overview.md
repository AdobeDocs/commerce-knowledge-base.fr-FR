---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.2'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.2.
exl-id: 6f8a7e74-b385-49f7-8032-fcaad8b252e9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.1.2 - Aperçu

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.2.

QPT v1.1.2 comprend les correctifs suivants :

1. **MDVA-37115** : corrige le problème qui entraînait l’affichage d’un avis inutile de *Il ne reste que 0&rbrace; sur la page du produit configurable.*
1. **MDVA-37364** : résolution du problème en raison duquel l’attribut personnalisé de type date rompt l’interface utilisateur de grille du client.
1. **MDVA-38447** : corrige deux problèmes : où les produits enfants configurables *Non visibles individuellement* sont renvoyés dans la réponse GraphQL et optimisez la requête MySQL pour les produits GraphQL avec filtre de catégorie.
1. **MDVA-38852** : résolution du problème en raison duquel l’inventaire des catalogues par conception verrouille les tables pour les mises à jour qui réduisent considérablement les performances dans le cas de plusieurs commandes parallèles.
1. **MDVA-38929** : correction d’un problème en raison duquel la facture avec FPT affichait un total général incorrect lorsque la commande était payée à partir du crédit de la boutique.
1. **MDVA-39043** : correction d’un problème en raison duquel l’utilisateur administrateur disposant d’un accès limité obtenait une erreur lors de la tentative d’ajout du widget *Products* à la page CMS.
1. **MDVA-39195** : correction du problème en raison duquel le bouton **[!UICONTROL Add to Cart]** était inactif sur la page de catégorie lorsque la redirection vers le panier était activée.
1. **MDVA-39384** : correction d’un problème en raison duquel l’attribut client personnalisé pour un utilisateur de la société n’était pas enregistré.
1. **MDVA-39521** : correction d’un problème en raison duquel l’utilisateur ne pouvait pas définir d’adresses de livraison sur le panier avec un numéro de téléphone vide via GraphQL.
1. **MDVA-39923** : correction d’un problème en raison duquel les clients obtenaient une erreur lorsqu’ils recherchaient la commande par SKU dans la fonctionnalité de commande rapide B2B avec une casse différente de celle avec laquelle le nom était enregistré.
1. **MDVA-39935** : résolution du problème en raison duquel GraphQL renvoie des produits enfants configurables désactivés au niveau du site web.
1. **MDVA-39966** : corrige le problème de déploiement de paramètres régionaux incorrects.
1. **MDVA-39986** : correction d’un problème en raison duquel l’utilisateur ne pouvait pas passer de commande dans Admin on MacOS à l’aide du navigateur Safari.
1. **MDVA-40134** : correction d’un problème en raison duquel GraphQL ne renvoyait pas de produits associés lorsque le catalogue partagé était activé.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
