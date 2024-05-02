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

# Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.37

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.37.

QPT v1.1.37 comprend les correctifs suivants :

1. **ACSD-52613**: corrige le problème d’actualisation des caches et des index même lorsqu’aucune mise à jour n’est effectuée sur `Inventory_source` éléments par l’API rest.
1. **ACSD-51884**: corrige le problème en raison duquel le chemin du cache de l’image du produit était incorrect après l’exécution de la commande resize.
1. **ACSD-53628**: correction d’un problème en raison duquel le rapport de commande client CSV affichait des caractères spéciaux incorrects.
1. **ACSD-49843**: corrige le problème en raison duquel le lien sur le téléchargement de produit n’est pas disponible une fois que l’article commandé est automatiquement facturé par le mode de paiement en ligne avec la variable *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* activée.
1. **ACSD-53148**: correction d’un problème en raison duquel deux demandes parallèles dans GraphQL pour l’ajout du même produit configurable au panier entraînaient l’affichage de deux éléments distincts dans le panier avec le même SKU de produit.
1. **ACSD-47054**: corrige le problème en raison duquel la réindexation de l’aperçu s’exécute pour tous les magasins, ce qui entraîne une lenteur.
1. **ACSD-52606**: corrige le problème lié au message d’erreur. *Votre commande n’est pas prête pour la récupération* s’affiche lorsque l’utilisateur clique **[!UICONTROL Notify Order is Ready for Pickup]**.
1. **ACSD-51574**: corrige le problème en raison duquel l’image n’est pas mise à jour sur le front-end après son remplacement par une autre image portant le même nom.
1. **ACSD-53728**: correction d’un problème en raison duquel l’indexeur EAV du produit prenait plus de temps à se terminer.
1. **ACSD-53979**: résout le problème JS qui se produit sur la page d’accueil si le message de bienvenue contient un guillemet simple.
1. **ACSD-52143**: corrige le problème de suppression des options personnalisées après l’importation du produit.
1. **ACSD-53750**: corrige la variable *Canalisation rompue ou connexion fermée* erreur lors d’une opération multi-thread `catalog_product_price` réindexer.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
