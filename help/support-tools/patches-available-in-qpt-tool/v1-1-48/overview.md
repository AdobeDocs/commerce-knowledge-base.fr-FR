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

# Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.48

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.48.

QPT v1.1.48 comprend les correctifs suivants :

1. **ACSD-55566**: corrige le problème en raison duquel la variable *[!UICONTROL mergeCart mutation]* échoue avec une *Erreur interne du serveur* dans la réponse GraphQL lors de la fusion des paniers source et de destination ont les mêmes éléments regroupés.
1. **ACSD-56546**: corrige le problème en raison duquel les produits configurables et regroupés s’affichaient comme *[!UICONTROL Out of Stock]* sur le storefront lorsque la variable *[!UICONTROL Display Out of Stock Product]* est désactivée.
1. **ACSD-56635**: corrige le problème de duplication du client importé avec la même adresse électronique lorsque l’importation est utilisée avec [!UICONTROL Account Sharing] défini sur *[!UICONTROL Global]*.
1. **ACSD-56741**: corrige le message d’erreur *Tentative d’accès au décalage du tableau sur la valeur de type null* qui s’affiche pendant `setup:upgrade` lorsque la base de données contient un déclencheur MySQL personnalisé qui n’est pas lié au mécanisme d’indexation et que [!DNL MView].
1. **ACSD-57315**: corrige le problème de création d’une transaction dans [!DNL PayPal Payflow Pro] chaque fois que la fonction **[!UICONTROL Fetch]** Cliquez sur le bouton dans l’écran d’affichage des transactions de la [!UICONTROL Admin].
1. **ACSD-57337**: correction d’un problème en raison duquel un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques pouvait voir des entreprises de tous les sites web dans la variable *[!UICONTROL Companies]* grid.
1. **ACSD-57394**: corrige le tri incorrect des produits selon plusieurs champs de tri dans GraphQL.
1. **ACSD-57565**: corrige le problème en raison duquel la variable *[!UICONTROL Order]* Le tableau de bord affiche des informations de commande incorrectes jusqu’à ce que la période soit mise à jour. Le tableau de bord affiche désormais les statistiques de commande correctes au premier chargement.
1. **ACSD-57854**: corrige le problème en raison duquel les demandes GraphQL de produits renvoyaient des catégories désactivées dans les agrégations de catégories.
1. **ACSD-58008**: corrige le problème en raison duquel la mise à jour d’une mise à jour planifiée supprimait la version précédente de l’élément intermédiaire si aucune date de fin n’était spécifiée.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.

