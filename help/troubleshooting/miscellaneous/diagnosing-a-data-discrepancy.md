---
title: Diagnostic d’une incohérence des données
description: Cet article fournit des solutions pour résoudre les problèmes d’incohérence entre un rapport de Magento Business Intelligence (MBI) et un rapport de requête ou tiers.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Diagnostic d’une incohérence des données

Cet article fournit des solutions pour résoudre les problèmes d’incohérence entre un rapport de Magento Business Intelligence (MBI) et un rapport de requête ou tiers.

En fonction de la complexité de votre analyse, la génération du rapport de l’IMS correspondant peut nécessiter une connaissance de plusieurs facettes de la plateforme. Cette liste de contrôle et les liens connexes vous aideront à comprendre la logique qui sous-tend votre rapport, ce qui vous permet d’identifier la source de toute incohérence.

1. Si un autre membre de votre équipe a créé le rapport, commencez par confirmer l’objectif et les paramètres de son analyse.
1. Générez les points de données attendus à comparer au rapport de l’IMS en fonction d’une requête, d’un outil de création de rapports tiers ou d’une formule.
1. Vérifiez et confirmez la ou les définitions [metric](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html), soit à partir du lien de mesure en Report Builder, soit en consultant l’onglet [Résumé système](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary) :
   * Table de données
   * Opération
   * La colonne &quot;Operand&quot;, y compris son calcul s’il est dérivé (via le résumé du système)
   * Horodatage
   * Pour les mesures d’abonnement : dates de début et de fin
   * Filtres, y compris ceux contenus dans tout [jeu de filtres](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html) appliqué
1. Examinez et confirmez d’autres manipulations de données dans le rapport :
   * Formules calculées
   * [Groupings](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html#groupby)
   * [Perspectives](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [Options de temps](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * Pour [l’analyse des cohortes](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis) : date de cohorte
   * Pour [l’analyse des cohortes](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis) : perspective des cohortes
1. Si la différence implique des données récentes, confirmez le dernier point de données disponible en consultant la section **Mettre à jour les détails** sur la page Connexions.
1. Si une mesure utilisée dans l’analyse est créée sur une table de votre base de données où des lignes ont jamais été supprimées de cette table, vérifiez auprès de l’équipe d’assistance IMS que la table est recherchée pour les lignes supprimées, ainsi que la fréquence de vérification et la [méthode de réplication](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) de la table.
1. De même, si les colonnes utilisées dans l’analyse peuvent être modifiées après l’ajout d’une ligne, vérifiez avec la prise en charge que ces colonnes sont [vérifiées pour modification](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html), ainsi que la fréquence du nouveau contrôle.

**Toujours bloquée ?** Ne vous inquiétez pas : nous sommes là pour aider. Envoyez-nous une demande en utilisant [ces instructions](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).

## Lecture connexe

[ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
