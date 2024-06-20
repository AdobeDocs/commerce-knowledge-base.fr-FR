---
title: Adobe Commerce [!DNL Site-Wide Analysis Tool] FAQ sur les rapports
description: En savoir plus sur les [!DNL Site-Wide Analysis Tool], un outil en libre-service proactif et un référentiel central qui comprend des informations détaillées sur le système et des recommandations pour garantir la sécurité et la maniabilité de votre installation Adobe Commerce.
exl-id: 7c843d55-9e2c-4b18-8859-0ebad0ae28cf
feature: Best Practices, Saas, Support, Tools and External Services
role: Admin
source-git-commit: 580ad148cd4346868cd9892a1ae9a4d85f73edce
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Adobe Commerce [!DNL Site-Wide Analysis Tool] FAQ sur les rapports

>[!IMPORTANT]
>
>À compter du 23 avril 2024, la [!DNL Site-Wide Analysis Tool] sera mis hors service pour tous les clients Adobe Commerce sur site.

Cet article décrit la variable [!DNL Site-Wide Analysis Tool] Rapport généré automatiquement pour Adobe Commerce sur les clients de l’infrastructure cloud, sur une base mensuelle ou trimestrielle.

>[!NOTE]
>
>Dans Adobe Commerce sur l’infrastructure cloud v2.4.1 et versions ultérieures, [!DNL Site-Wide Analysis Tool] est disponible via le panneau d’administration de Commerce. Par conséquent, [!DNL Site-Wide Analysis Tool] Les rapports peuvent être exécutés directement par le client. Pour plus d’informations sur l’accès, reportez-vous au [[!DNL Site-Wide Analysis Tool] guide](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/access.html).

## Présentation [!DNL Site-Wide Analysis Tool]?

[!DNL Site-Wide Analysis Tool] est une application SaaS qui effectue une analyse de site client &quot;point dans le temps&quot; de bout en bout (dans la variable [!DNL Site-Wide Analysis Tool] , et non sur le site du client). Tous [!DNL Site-Wide Analysis Tool]Les informations relatives au site client sont collectées selon des calendriers prédéterminés toutes les 3 heures à une fois par jour. Cela signifie que [!DNL Site-Wide Analysis Tool] analyse constamment les données du site client pour en savoir plus.

## Qu’est-ce qu’une [!DNL Site-Wide Analysis Tool] Rapport ?

La variable [!DNL Site-Wide Analysis Tool] Rapport est une liste de résultats (problèmes) avec des recommandations de bonnes pratiques en libre-service, qui peuvent être envoyées aux clients sous forme de PDF par le biais du système de tickets d’assistance Adobe Commerce.

## Quelles informations sont incluses dans une [!DNL Site-Wide Analysis Tool] Rapport ?

Les informations du site, fournies dans la variable [!DNL Site-Wide Analysis Tool] inclut :

* Recherche
   * Aperçu, y compris une &quot;priorité&quot; pour l’ordre de correctif de mise en oeuvre
   * Description de recherche
   * Conditions préalables, le cas échéant
   * Impact(s) sur le site
   * Cause(s) racine(s)
   * Recommandations
* Journaux des exceptions
   * Informations sur l’exception de journal
   * Date de la dernière occurrence
   * Nombre de fois où l’exception se produit

## Qui reçoit le mensuel automatisé [!DNL Site-Wide Analysis Tool] rapports ?

Actuellement, les clients qui ont une [!DNL Site-Wide Analysis Tool] L’index d’intégrité (au niveau ou en dessous du seuil de performance actuellement défini) recevra un [!DNL Site-Wide Analysis Tool] Créez des rapports pour leur environnement de production via le système de tickets d’assistance.

## Qui reçoit le trimestriel automatisé [!DNL Site-Wide Analysis Tool] rapports ?

Tous les clients, quel que soit le [!DNL Site-Wide Analysis Tool] l’indice de santé, qui recevra un trimestriel [!DNL Site-Wide Analysis Tool] Créez des rapports pour leur environnement de production via le système de tickets d’assistance.

## Comment les rapports sont-ils distribués ?

[!DNL Site-Wide Analysis Tool] les rapports sont livrés automatiquement par le biais du système de ticket d’assistance d’Adobe Commerce, tous les mois ou tous les trimestres. [!DNL Site-Wide Analysis Tool] les rapports peuvent également être générés manuellement à partir de la variable [!DNL Site-Wide Analysis Tool] Tableau de bord et enregistré sur votre bureau. Ces [!DNL Site-Wide Analysis Tool] les rapports peuvent ensuite être envoyés par courrier électronique en tant que pièces jointes.

>[!NOTE]
>
>Après l’application d’une recommandation, la génération manuelle d’un rapport ne met pas à jour les recommandations. La suppression d’un rapport peut prendre quelques jours. [!DNL Site-Wide Analysis Tool Dashboard].
