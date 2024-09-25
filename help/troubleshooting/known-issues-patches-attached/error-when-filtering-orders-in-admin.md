---
title: Erreur lors du filtrage des commandes dans l’administrateur
description: Cet article fournit un correctif pour le problème Adobe Commerce, où une erreur se produit lors de la tentative de filtrage des commandes dans l’administrateur par date, affichant le message "Violation de la contrainte d’intégrité 1052 Column 'created_at' où la clause est ambiguë".
feature: Orders
role: Developer
source-git-commit: e5eb65b23afaed4658f8576c747f11a31a8ec1aa
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Erreur lors du filtrage des commandes dans l’administrateur

Cet article fournit un correctif pour le problème Adobe Commerce où une erreur se produit lors de la tentative de filtrage des commandes dans l’administrateur par date, affichant le message : *Violation de contrainte d’intégrité : 1052 Colonne &#39;created_at&#39; où la clause est ambiguë*.

## Versions affectées

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7

## Problème

Le filtrage des commandes dans l’Admin par date renvoie une erreur.

Le fichier exception.log affiche :

```SQL
report.CRITICAL: PDOException: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'created_at' in where clause is ambiguous in /path/to/magento/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
```

<u>Étapes à reproduire :</u>

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
   * Définir l’ordre de **[!UICONTROL Purchase Date Ascending]** dans la grille OU
   * Définissez **[!UICONTROL Purchase Date Filter]** dans les filtres.

1. Une erreur s’affiche : *Une erreur s’est produite lors du traitement de la vue par défaut et nous avons restauré le filtre à son état d’origine.*

## Cause

Il existe un problème avec les modules [!DNL PayPal Braintree].

## Solution

Pour résoudre le problème, appliquez le correctif joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[bundle_3357_filter_order_in_admin_by_date_patch.zip](assets/bundle-3357-unable-to-filter-order-in-admin-by-date.zip)

Le correctif est compatible avec toutes les versions et éditions concernées.

## Comment appliquer le correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans la base de connaissances de support.
