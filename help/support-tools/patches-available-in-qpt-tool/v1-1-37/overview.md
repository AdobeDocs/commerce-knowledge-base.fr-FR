---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.37'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.37.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4ccdba38-8171-4cc4-b8ef-d2c53dec0b47
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.37

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.37.

QPT v1.1.37 comprend les correctifs suivants :

1. **ACSD-52613** : résolution du problème d’actualisation des caches et des index même lorsqu’aucune mise à jour n’est effectuée sur les éléments `Inventory_source` par l’API REST.
1. **ACSD-51884** : résolution du problème de l’erreur de chemin d’accès au cache de l’image du produit après l’exécution de la commande resize.
1. **ACSD-53628** : correction d’un problème en raison duquel le rapport de commande client CSV affichait des caractères spéciaux incorrects.
1. **ACSD-49843** : résolution du problème en raison duquel le lien de téléchargement de produit n’est pas disponible une fois que l’article commandé est automatiquement facturé par le mode de paiement en ligne avec le paramètre *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* activé.
1. **ACSD-53148** : résolution du problème en raison duquel deux demandes parallèles dans GraphQL pour l’ajout du même produit configurable au panier entraînaient deux articles distincts dans le panier avec le même SKU de produit.
1. **ACSD-47054** : résolution du problème en raison duquel la réindexation de l’aperçu s’exécute pour tous les magasins, ce qui entraîne une lenteur.
1. **ACSD-52606** : correction d’un problème en raison duquel le message d’erreur *Votre commande n’est pas prête pour la récupération* s’affichait lorsque l’utilisateur cliquait sur **[!UICONTROL Notify Order is Ready for Pickup]**.
1. **ACSD-51574** : résolution du problème en raison duquel l’image n’est pas mise à jour sur le front-end après son remplacement par une autre image portant le même nom.
1. **ACSD-53728** : correction d’un problème en raison duquel l’indexeur EAV du produit prenait plus de temps à se terminer.
1. **ACSD-53979** : corrige le problème JS qui se produit sur la page d’accueil si le message de bienvenue contient une seule citation.
1. **ACSD-52143** : résolution du problème de suppression des options personnalisées après l’importation du produit.
1. **ACSD-53750** : corrige l’erreur *de pipeline rompu ou de connexion fermée* lors d’une réindexation `catalog_product_price` multi-thread.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
