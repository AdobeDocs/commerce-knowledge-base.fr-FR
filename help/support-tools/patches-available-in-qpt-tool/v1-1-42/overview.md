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

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.42

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.42.

QPT v1.1.42 comprend les correctifs suivants :

1. **ACSD-53658** : correction d’un problème en raison duquel les données de produit *[!UICONTROL Recently Viewed]* n’étaient pas mises à jour correctement dans la vue de magasin.
1. **ACSD-54626** : résolution du problème de l’impossibilité de créer une règle de bon de commande (`createPurchaseOrderApprovalRule`) avec l’attribut `NUMBER_OF_SKUS` via GraphQL.
1. **ACSD-53845** : résolution du problème de délai d’expiration de la connexion MySQL lorsque `consumer max_messages` = 0.
1. **ACSD-54890** : correction d’un problème en raison duquel `aggregate_sales_report_bestsellers_data` provoquait des erreurs MySQL en raison d’une insuffisance d’espace disque de `/tmp`.
1. **ACSD-55112** : correction d’un problème en raison duquel il était possible de cliquer plusieurs fois sur le bouton *[!UICONTROL Submit review]* sans validation [!DNL Google reCAPTCHA v3].
1. **ACSD-54264** : résolution du problème en raison duquel le message d’erreur *Vous ne pouvez pas mettre à jour l’attribut demandé. Identifiant de ligne : store_id* s’affiche lorsqu’un client tente d’extraire avec un guillemet négociable provenant d’une autre vue de magasin.
1. **ACSD-54418** : corrige le problème qui entraînait l’application incorrecte d’un montant fixe de remise à chaque produit enfant du lot à prix dynamique.
1. **ACSD-55238** : résolution du problème d’enregistrement de la méta-description de produit vide.
1. **ACSD-54966** : correction d’un problème en raison duquel le code d’un coupon ayant une utilisation limitée par client ne pouvait pas être réutilisé en cas d’échec de la commande précédente.
1. **ACSD-54060** : résolution du problème où un administrateur restreint ne peut pas enregistrer un produit s’il est un enfant d’un autre produit affecté à une portée différente.
1. **ACSD-48910** : correction d’un problème en raison duquel un produit groupé affecté à plusieurs sources était en rupture de stock après la facturation et l’expédition d’une commande, même s’il a une quantité non nulle.
1. **ACSD-55381** : corrige une erreur de serveur interne lors de l’interrogation des champs `configurable_product_option_uid` et `configurable_product_option_value_uid` à partir d’un B2B *[!UICONTROL Requisition list]* via GraphQL.
1. **ACSD-55628** : correction du téléchargement d’un fichier sur le formulaire d’enregistrement de la société et du remplacement d’un fichier pour un attribut du client sur le storefront.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
