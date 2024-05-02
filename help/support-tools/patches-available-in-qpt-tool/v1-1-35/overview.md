---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.35'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.35.
feature: Tools and External Services
role: Admin
exl-id: 46228690-44ce-462f-b700-1aea6fa0eeab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.35

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.35.

QPT v1.1.35 comprend les correctifs suivants :

1. **ACSD-51899**: corrige le problème en raison duquel l’adresse de livraison par défaut à l’étape d’expédition du passage en caisse est automatiquement renseignée avec une adresse de récupération en magasin précédemment sélectionnée.
1. **ACSD-52041**: corrige le problème lié au message d’erreur : *[ERROR] [!DNL Page Builder] était rendu pendant 5 secondes sans déverrouiller*. apparaît dans [!DNL Chrome] navigateur lors de l’enregistrement de contenu modifié avec [!DNL Page Builder].
1. **ACSD-52095**: corrige le problème en raison duquel la variable `manage_stock` était incorrectement définie sur 0 dans le fichier CSV après l’exportation du produit.
1. **ACSD-51358**: corrige le problème en raison duquel la suppression d’une mise à jour planifiée sans date de fin entraîne la suppression d’autres mises à jour planifiées pour la même entité.
1. **ACSD-48070**: corrige le problème en raison duquel la modification d’une mise à jour planifiée déclenche une exception.
1. **ACSD-51890**: corrige le problème en raison duquel la variable [!UICONTROL Submit review] peut être cliqué plusieurs fois sans [!DNL Google] validation reCAPTCHA v3.
1. **ACSD-51984**: corrige le problème si non coché. *Utiliser la valeur par défaut et des valeurs de champ de produit autres que celles par défaut* ne sont pas enregistrés pour le deuxième affichage de site web, de magasin et de magasin.
1. **ACSD-52398**: corrige l’erreur *La quantité demandée n’est pas disponible.* qui se produit lors de la tentative de mise à jour de la quantité d’un produit regroupé dans le panier sur le storefront.
1. **ACSD-52786**: corrige le problème d’application d’un SKU de condition de règle de catalogue à tous les produits commençant par le SKU donné.
1. **ACSD-52921**: corrige le problème d’erreur interne qui se produisait lors de la demande de détails de panier auprès de GraphQL lorsqu’un produit configurable en rupture de stock se trouvait dans le panier.
1. **ACSD-51683**: correction d’un problème en raison duquel une option personnalisable ne pouvait pas être ajoutée au panier à l’aide de GraphQL.
1. **ACSD-52133**: correction d’un problème en raison duquel un compte client ne pouvait pas être enregistré après une mise à niveau.
1. **ACSD-52202**: corrige le problème en raison duquel la quantité vendable du stock par défaut passe incorrectement à 0 lorsqu’un stock autre que celui par défaut est remplacé par 0 quantité lors de l’exécution de la commande.
1. **ACSD-51265**: corrige le problème avec `catalog_product_price` réindexation des performances lorsqu’il y a trop de produits regroupés dans le système.
1. **ACSD-52831**: correction d’un problème en raison duquel les clients ne pouvaient pas envoyer de devis négociables lors de la [!DNL Google reCAPTCHA v3 Invisible] est activée.
1. **ACSD-51845**: corrige le problème en raison duquel les produits suivants avec des prix de niveau et différents ensembles d’attributs ne peuvent pas être mis à jour via l’API REST en bloc asynchrone.
1. **ACSD-52815**: corrige le problème en raison duquel l’entrée du champ de quantité d’une source autre que par défaut ne prend en charge que 6 chiffres au maximum, à la différence de 8 pour un stock par défaut.
1. **ACSD-51149**: résout le problème en raison duquel [!UICONTROL Scheduled ImportExport] avec activé [!UICONTROL Catalog Permissions] invalide les indexeurs, puis vide le cache par cron.
1. **ACSD-50815**: corrige le problème en raison duquel la quantité décimale d’un produit simple ne peut pas être utilisée pour une nouvelle option de produit groupé.
1. **ACSD-52399**: corrige le problème d’affichage de l’option de produit configurable avec une valeur de Qté vendable de 0. *En stock* sur la page produit.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
