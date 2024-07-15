---
title: Adobe Commerce [!DNL Site-Wide Analysis Tool] FAQ sur les rapports
description: Découvrez  [!DNL Site-Wide Analysis Tool], un outil en libre-service proactif et un référentiel central qui comprend des informations détaillées sur le système et des recommandations pour garantir la sécurité et la maniabilité de votre installation Adobe Commerce.
exl-id: 7c843d55-9e2c-4b18-8859-0ebad0ae28cf
feature: Best Practices, Saas, Support, Tools and External Services
role: Admin
source-git-commit: 580ad148cd4346868cd9892a1ae9a4d85f73edce
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# FAQ sur le rapport Adobe Commerce [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>À compter du 23 avril 2024, le [!DNL Site-Wide Analysis Tool] sera mis hors service pour tous les clients Adobe Commerce sur site.

Cet article décrit le rapport [!DNL Site-Wide Analysis Tool] généré automatiquement pour Adobe Commerce sur les clients de l’infrastructure cloud sur une base mensuelle ou trimestrielle.

>[!NOTE]
>
>Dans Adobe Commerce sur l’infrastructure cloud v2.4.1 et versions ultérieures, [!DNL Site-Wide Analysis Tool] est disponible via le panneau d’administration de Commerce. Par conséquent, les rapports [!DNL Site-Wide Analysis Tool] peuvent être exécutés directement par le client. Pour plus d&#39;informations sur l&#39;accès, consultez le [[!DNL Site-Wide Analysis Tool] guide](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/access.html).

## Qu’est-ce que [!DNL Site-Wide Analysis Tool] ?

[!DNL Site-Wide Analysis Tool] est une application SaaS qui effectue une analyse de site client &quot;point dans le temps&quot; de bout en bout (dans l’environnement [!DNL Site-Wide Analysis Tool], et non sur le site du client). Toutes les informations sur le site client [!DNL Site-Wide Analysis Tool] sont collectées selon des calendriers prédéterminés toutes les 3 heures à une fois par jour. Cela signifie que [!DNL Site-Wide Analysis Tool] analyse constamment les données du site client à la recherche de résultats.

## Qu’est-ce qu’un rapport [!DNL Site-Wide Analysis Tool] ?

Le rapport [!DNL Site-Wide Analysis Tool] est une liste de résultats (problèmes) avec des recommandations de bonnes pratiques en libre-service, qui peuvent être envoyées aux clients sous forme de PDF par le biais du système de tickets d’assistance Adobe Commerce.

## Quelles informations sont incluses dans un rapport [!DNL Site-Wide Analysis Tool] ?

Les informations sur le site, fournies dans le rapport [!DNL Site-Wide Analysis Tool], incluent :

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

## Qui reçoit les rapports mensuels automatisés [!DNL Site-Wide Analysis Tool] ?

Actuellement, les clients ayant un indice d’intégrité [!DNL Site-Wide Analysis Tool] faible (à ou en dessous du seuil de performance actuellement défini) recevront un rapport [!DNL Site-Wide Analysis Tool] mensuel pour leur environnement de production via le système de tickets d’assistance.

## Qui reçoit les rapports trimestriels automatisés [!DNL Site-Wide Analysis Tool] ?

Tous les clients, quel que soit l’indice d’intégrité [!DNL Site-Wide Analysis Tool], recevront un rapport trimestriel [!DNL Site-Wide Analysis Tool] pour leur environnement de production par le biais du système de tickets d’assistance.

## Comment les rapports sont-ils distribués ?

Les rapports [!DNL Site-Wide Analysis Tool] sont livrés automatiquement via le système de tickets d&#39;assistance Adobe Commerce tous les mois ou tous les trimestres. Les rapports [!DNL Site-Wide Analysis Tool] peuvent également être générés manuellement à partir du tableau de bord [!DNL Site-Wide Analysis Tool] et enregistrés sur votre bureau. Ces [!DNL Site-Wide Analysis Tool] rapports peuvent ensuite être envoyés par courrier électronique en tant que pièces jointes.

>[!NOTE]
>
>Après l’application d’une recommandation, la génération manuelle d’un rapport ne met pas à jour les recommandations. Il peut s’écouler quelques jours avant qu’il ne soit supprimé du [!DNL Site-Wide Analysis Tool Dashboard].
