---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.42'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.42.
feature: Tools and External Services
role: Admin, Developer
exl-id: 49f7ebd6-7a5f-49da-8fac-c3c2b73b52c1
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.42

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.42.

QPT v1.1.42 comprend les correctifs suivants :

1. **ACSD-53658**: résout le problème en raison duquel *[!UICONTROL Recently Viewed]* les données de produit ne sont pas mises à jour correctement dans la vue magasin.
1. **ACSD-54626**: corrige le problème qui empêchait la création d’une règle de bon de commande (`createPurchaseOrderApprovalRule`) avec la fonction `NUMBER_OF_SKUS` via GraphQL.
1. **ACSD-53845**: corrige le problème de délai d’expiration de la connexion MySQL lors de la `consumer max_messages` = 0.
1. **ACSD-54890**: résout le problème en raison duquel `aggregate_sales_report_bestsellers_data` provoque des erreurs MySQL en raison de `/tmp` Le disque manque d’espace.
1. **ACSD-55112**: corrige le problème en raison duquel la variable *[!UICONTROL Submit review]* peut être cliqué plusieurs fois sans [!DNL Google reCAPTCHA v3] validation.
1. **ACSD-54264**: corrige le problème lié au message d’erreur. *Vous ne pouvez pas mettre à jour l’attribut requis. Identifiant de ligne : store_id* apparaît lorsqu’un client tente d’extraire avec un devis négociable provenant d’une autre vue de magasin.
1. **ACSD-54418**: corrige le problème qui entraînait l’application incorrecte d’un montant fixe de remise à chaque produit enfant du lot à prix dynamique.
1. **ACSD-55238**: corrige le problème lors de l’enregistrement de la méta-description de produit vide.
1. **ACSD-54966**: corrige le problème en raison duquel le code d’un coupon ayant une utilisation limitée par client ne peut pas être réutilisé en cas d’échec de la commande précédente.
1. **ACSD-54060**: correction d’un problème en raison duquel un administrateur restreint ne pouvait pas enregistrer un produit s’il s’agissait d’un enfant d’un autre produit affecté à une autre portée.
1. **ACSD-48910**: corrige le problème en raison duquel un produit regroupé affecté à plusieurs sources est en rupture de stock après la facturation et l’expédition d’une commande, même s’il a une quantité non nulle.
1. **ACSD-55381**: corrige une erreur de serveur interne lors de l’interrogation `configurable_product_option_uid` et `configurable_product_option_value_uid` champs d’un B2B *[!UICONTROL Requisition list]* via GraphQL.
1. **ACSD-55628**: corrige le téléchargement d’un fichier sur le formulaire d’enregistrement de la société et le remplacement d’un fichier pour un attribut du client sur le storefront.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
