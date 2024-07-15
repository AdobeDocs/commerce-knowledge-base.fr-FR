---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.48'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.48.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6170c616-312c-4de3-98dc-e2c27c376608
source-git-commit: 42712af2ce4337cd64b8dea555139e4252fb91cf
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.48

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.48.

QPT v1.1.48 comprend les correctifs suivants :

1. **ACSD-55566** : résolution du problème d’échec de *[!UICONTROL mergeCart mutation]* avec une *erreur interne du serveur* dans la réponse GraphQL lors de la fusion des paniers source et destination ayant les mêmes éléments regroupés.
1. **ACSD-56546** : résolution du problème d’affichage de *[!UICONTROL Out of Stock]* sur le storefront des produits configurables et groupés lorsque la configuration *[!UICONTROL Display Out of Stock Product]* est désactivée.
1. **ACSD-56635** : résolution du problème de duplication du client importé avec la même adresse électronique lorsque l’importation est utilisée avec [!UICONTROL Account Sharing] défini sur *[!UICONTROL Global]*.
1. **ACSD-56741** : corrige le message d’erreur *Tentative d’accès au décalage de tableau sur la valeur de type null* qui s’affiche pendant `setup:upgrade` lorsque la base de données contient un déclencheur MySQL personnalisé qui n’est pas lié au mécanisme d’indexation et [!DNL MView].
1. **ACSD-57315** : corrige le problème de création d’une transaction dans [!DNL PayPal Payflow Pro] chaque fois que l’utilisateur clique sur le bouton **[!UICONTROL Fetch]** dans l’écran d’affichage des transactions dans [!UICONTROL Admin].
1. **ACSD-57337** : correction d’un problème en raison duquel un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques pouvait voir des entreprises de tous les sites web dans la grille *[!UICONTROL Companies]*.
1. **ACSD-57394** : corrige le tri incorrect des produits selon plusieurs champs de tri dans GraphQL.
1. **ACSD-57565** : correction d’un problème en raison duquel le tableau de bord *[!UICONTROL Order]* affichait des informations de commande incorrectes jusqu’à la mise à jour de la période. Le tableau de bord affiche désormais les statistiques de commande correctes au premier chargement.
1. **ACSD-57854** : résolution du problème en raison duquel les demandes GraphQL de produit renvoient des catégories désactivées dans les agrégations de catégories.
1. **ACSD-58008** : résolution du problème en raison duquel la mise à jour d’une mise à jour planifiée supprime la version précédente de l’élément intermédiaire si aucune date de fin n’est spécifiée.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.

