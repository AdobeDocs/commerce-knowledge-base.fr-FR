---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.31.
exl-id: 0d93619e-0ae6-4dba-9b76-8aeb026c456d
feature: Tools and External Services
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.31

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.31.

QPT v1.1.31 comprend les correctifs suivants :

1. **ACSD-50817** : optimise l’exécution plus rapide de la tâche cron `sales_clean_quotes` en ajoutant un index composite sur les colonnes `store_id` et `updated_at` dans la table des guillemets.
1. **ACSD-50345** : résolution du problème où : [!DNL Google reCAPTCHA v2] ne se recharge pas après l’envoi d’un paiement en échec, [!DNL Google reCAPTCHA v3 Invisible] ne fonctionne pas lors de l’extraction et la commande ne peut pas être placée, et l’événement [!UICONTROL PlaceOrder] n’a pas été déclenché.
1. **ACSD-49392** : résolution du problème en raison duquel l’état de la commande se ferme après un remboursement partiel d’un produit fourni.
1. **ACSD-51036** : résolution du problème en raison duquel les conditions de concurrence lors d’appels d’API REST simultanés entraînent le remplacement des informations d’état d’expédition dans la table [!UICONTROL Items Ordered].
1. **ACSD-50858** : corrige le problème en raison duquel un coupon est incorrectement marqué comme utilisé après l’échec du paiement de la carte.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
