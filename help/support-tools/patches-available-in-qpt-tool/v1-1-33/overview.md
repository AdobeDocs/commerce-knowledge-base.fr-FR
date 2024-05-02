---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.33'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.3.
feature: Tools and External Services
role: Admin
exl-id: df3ae5e2-7c57-4ccd-af34-eb78cc60bcf6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.33

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.3.

QPT v1.1.33 comprend les correctifs suivants :

1. **ACSD-50478**: corrige la commande de restauration de base de données dans le cas où le fichier de sauvegarde DB contient des déclencheurs et une commande SQL de délimiteur.
1. **ACSD-50512**: corrige l’erreur : *Le lien téléchargeable n’est pas lié au produit. Vérifiez le lien et réessayez.*  qui se produit lors de la mise à jour de la date de début d’une mise à jour intermédiaire de produit téléchargeable.
1. **ACSD-50949**: corrige le problème en raison duquel le filtre de prix dans [!UICONTROL Advanced Search] ne renvoie pas de résultats appropriés lorsqu’il est utilisé le long du filtre SKU.
1. **ACSD-51645**: corrige l’erreur générée lors de l’enregistrement d’une nouvelle [!UICONTROL Cart Price Rule] si l’extension `Magento_OfflineShipping` est désactivée.
1. **ACSD-50895**: résout le problème en raison duquel [!DNL Google Analytics] Les balises GTM 3 ne sont pas déclenchées si [!DNL Google Analytics] 4 GTM n’est pas configuré.
1. **ACSD-51102**: corrige le problème en raison duquel une règle de catalogue appliquée à un grand nombre de produits n’est pas correctement indexée lorsque la règle est activée par une mise à jour planifiée.
1. **ACSD-50368**: corrige le problème en raison duquel le rapport `group_id` est ignoré lorsqu’un client est créé par le biais de l’API REST asynchrone ou de l’API REST en bloc asynchrone.
1. **ACSD-51497**: correction d’un problème en raison duquel un client ne pouvait pas trier une page de catalogue par [!UICONTROL Custom Attribute] du type de liste déroulante.
1. **ACSD-51408**: corrige le problème en raison duquel l’état de l’élément de commande n’est pas correctement défini sur [!UICONTROL Backordered].
1. **ACSD-51735**: corrige le problème en raison duquel l’état de l’élément de commande n’est pas correctement défini sur [!UICONTROL Ordered] lorsque le stock de produit est *0*.
1. **ACSD-51792**: corrige le problème en raison duquel une page ne comporte pas l’événement d’impression lors de la [!DNL Google Tag Manager] 4 est activé.
1. **ACSD-51471**: correction d’un problème en raison duquel un utilisateur administrateur ne pouvait pas enregistrer une mise à jour planifiée pour un produit groupé qui utilise un produit simple dont la mise à jour est planifiée.
1. **ACSD-51700**: corrige l’erreur qui se produit lors du changement de vues de magasin sur une page de modification de produit téléchargeable dans l’administrateur.
1. **ACSD-51120**: correction d’un problème en raison duquel le cache des demandes de GET GraphQL n’était pas effacé pour les pages CMS contenant des blocs CMS mis à jour par le biais d’une mise à jour intermédiaire.
1. **ACSD-51240**: corrige le problème d’absence du fichier téléchargé si l’enregistrement est effectué via le formulaire d’enregistrement de l’entreprise.
1. **ACSD-51907**: correction d’un problème qui empêchait un utilisateur administrateur restreint de créer une note de crédit avec un remboursement hors ligne.
1. **ACSD-52148**: corrige le problème en raison duquel la variable [!UICONTROL Google V3 reCAPTCHA Admin] la connexion échoue parfois.
1. **ACSD-51431**: corrige le problème de fonctionnement d’un état d’indexeur même s’il n’y a pas de nouvelles entrées dans le journal des modifications.
1. **ACSD-51892**: corrige le problème de performances en raison duquel les fichiers de configuration se chargent plusieurs fois pendant le déploiement.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
