---
title: Diagnostic d’une incohérence des données
description: Cet article fournit des solutions pour résoudre les problèmes d’incohérence entre un rapport de Magento Business Intelligence (MBI) et un rapport de requête ou tiers.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Diagnostic d’une incohérence des données

Cet article fournit des solutions pour résoudre les problèmes d’incohérence entre un rapport de Magento Business Intelligence (MBI) et un rapport de requête ou tiers.

En fonction de la complexité de votre analyse, la génération du rapport de l’IMS correspondant peut nécessiter une connaissance de plusieurs facettes de la plateforme. Cette liste de contrôle et les liens connexes vous aideront à comprendre la logique qui sous-tend votre rapport, ce qui vous permet d’identifier la source de toute incohérence.

1. Si un autre membre de votre équipe a créé le rapport, commencez par confirmer l’objectif et les paramètres de son analyse.
1. Générez les points de données attendus à comparer au rapport de l’IMS en fonction d’une requête, d’un outil de création de rapports tiers ou d’une formule.
1. Vérifiez et confirmez [metric](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html) définition(s), soit à partir du lien de mesure en Report Builder, soit en visitant la [Résumé du système](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary) tab :
   * Table de données
   * Opération
   * La colonne &quot;Operand&quot;, y compris son calcul s’il est dérivé (via le résumé du système)
   * Horodatage
   * Pour les mesures d’abonnement : dates de début et de fin
   * Les filtres, y compris ceux contenus dans les [ensembles de filtres](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html) appliqué
1. Examinez et confirmez d’autres manipulations de données dans le rapport :
   * Formules calculées
   * [Groupements](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html#groupby)
   * [Perspectives](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [Options d’heure](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * Pour [analyse des cohortes](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Date de cohorte
   * Pour [analyse des cohortes](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): perspective des cohortes
1. Si l’incohérence concerne des données récentes, confirmez le dernier point de données disponible en consultant le **Détails de la mise à jour** sur la page Connexions .
1. Si une mesure utilisée dans l’analyse est créée sur un tableau de votre base de données où des lignes ont jamais été supprimées de ce tableau, vérifiez auprès de l’équipe d’assistance du MBI que le tableau est analysé pour les lignes supprimées, ainsi que la fréquence de la nouvelle vérification et de la fréquence. [méthode de réplication](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) pour la table.
1. De même, si les colonnes utilisées dans l’analyse peuvent être modifiées après l’ajout d’une ligne, vérifiez avec la prise en charge que ces colonnes sont en cours. [vérifié pour les modifications](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html), ainsi que la fréquence du nouveau contrôle.

**Toujours sur la sellette ?** Ne vous inquiétez pas, nous sommes ici pour aider. Envoyez-nous une requête en utilisant [ces instructions](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).
