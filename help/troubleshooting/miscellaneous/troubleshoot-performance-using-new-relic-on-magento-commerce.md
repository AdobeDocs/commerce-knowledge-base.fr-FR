---
title: Résolution des problèmes de performances à l’aide de New Relic sur Adobe Commerce
description: 'Cet article fournit des étapes de dépannage pour résoudre les problèmes de performances de l’infrastructure cloud d’Adobe Commerce à l’aide de New Relic. Il fournit également des ressources pour plus d’informations. Voici une liste des problèmes. Cliquez pour voir les étapes de dépannage dans notre base de connaissances du support :'
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Résolution des problèmes de performances à l’aide de New Relic sur Adobe Commerce

Cet article fournit des étapes de dépannage pour résoudre les problèmes de performances de l’infrastructure cloud d’Adobe Commerce à l’aide de New Relic. Il fournit également des ressources pour plus d’informations. Les problèmes suivants, abordés dans le tableau ci-dessous avec les ressources recommandées, sont les suivants :

* Score Apdex faible
* Utilisation élevée de CPU
* Opérations d’E/S élevées
* Panne

<table>
<tbody>
<tr>
<td>Problème</td>
<td>Dépannage</td>
<td>Ressources</td>
</tr>
<tr>
<td>
<p>Faible score Apdex :</p>
<p>Votre New Relic <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction">score Apdex</a> mesure la satisfaction des utilisateurs quant au temps de réponse de vos applications et services web.</p>
</td>
<td>
<p>Vous vous connectez à <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Aperçu. Sur le côté droit de la page Aperçu se trouve le graphique de score Apdex . Un score Apdex de 0,5 ou moins est un point d’inquiétude et nécessite une enquête : temps de transaction web (requêtes serveur) :</p>
<ol>
<ol>
<li>Connectez-vous à <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (Sélectionnez une application) &gt; Aperçu. Assurez-vous que le filtre est défini sur l’heure des transactions web dans le filtre déroulant du graphique principal. Ci-dessous, dans le tableau Transactions , recherchez l’heure du serveur d’applications. Vérifiez si vous avez des transactions suspectes ou en cours depuis longtemps.</li>
<li>Examinez-les individuellement en accédant à Surveillance &gt; Transactions et veillez à définir les filtres pour Web et Les plus longs<em>.</em>
</li>
<li>Recherchez ensuite les modules tiers qui consomment des ressources : fournisseurs de paiements, ERP, etc.</li>
<li>Dans la section Surveillance d’APM :<ol>
<li>Cliquez sur Transactions.</li>
<li>Faites défiler la page vers le bas, puis cliquez sur Afficher le tableau des transactions.</li>
<li>Vous pouvez trier les transactions en <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view">divers paramètres</a> et accéder à celles qui émettent des soupçons.</li>
<li>Passez en revue les transactions ayant un score Apdex faible, un nombre inhabituellement élevé, un temps moyen élevé ou un pourcentage de retard.</li>
<li>Cliquez sur chaque transaction individuelle. Si vous ne pouvez pas résoudre le problème, <a href="https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket">soumettez un ticket d’assistance.</a>
</li>
<li>Si vous devez effectuer des recherches plus approfondies, pensez à vérifier les transactions non Web.</li>
</ol>
</li>
</ol>
</ol>
<p>Temps hors transaction web (opérations et tâches en arrière-plan) :</p>
<ol>
<ol>
<li>Connectez-vous à <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (Sélectionnez une application) &gt; Aperçu. Veillez à sélectionner Durée des transactions non-web dans le filtre déroulant du graphique principal. Cliquez sur des transactions individuelles dans le tableau Transactions. Recherchez les transactions suspectes ou de longue durée. Cela inclut les tâches principales, les tâches cron ou les tâches d’importation/exportation, y compris les tâches tierces.</li>
</ol>
</ol>
</td>
<td>
<p>Pour en savoir plus sur le score New Relic Apdex, consultez la <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction">Documentation New Relic &gt; Apdex APM &gt; Mesurer la satisfaction des utilisateurs</a>. Vous pouvez également consulter <a href="https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-apdex-warning-alert">Alertes gérées pour Adobe Commerce : Alerte d’avertissement Apdex</a> dans notre base de connaissances d’assistance.</p>
</td>
</tr>
<tr>
<td>
<p>Utilisation élevée de CPU :</p>
<p>Une utilisation élevée de CPU peut indiquer qu’il existe un service particulièrement chargé, comme MySQL, Redis, etc.</p>
</td>
<td>
<ol>
<li>Connectez-vous à <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastructure &gt; Processus.</li>
<li>Consultez les graphiques CPU pour voir s’il existe un processus bloqué ou gourmand en temps de CPU supérieur à 100 % et comparez-le au nombre de processeurs sur l’instance. Prêtez attention aux pics d'utilisation des ressources. Il n’est pas recommandé de tuer un processus, sauf s’il s’agit d’un cron bloqué.</li>
</ol>
</td>
<td>
<p>Pour en savoir plus sur les mesures de performances, en particulier le pourcentage de CPU, les octets d'E/S et l'utilisation de la mémoire pour des individus ou des groupes de processus, consultez <a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes">Documentation de New Relic &gt; Page de l'interface utilisateur de l'infrastructure &gt; Page de l'hôte de l'infrastructure &gt; Onglet Processus</a>.</p>
</td>
</tr>
<tr>
<td>
<p>Opérations d’E/S élevées : pour chaque client, ce nombre est individuel, mais considérablement différent de la moyenne.</p>
</td>
<td>
<p>Recherchez un pic inhabituel par rapport aux opérations d’E/S moyennes précédentes :</p>
<ol>
<li>Connectez-vous à <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastructure &gt; Processus.</li>
<li>Graphique Vérifier les octets de lecture d’E/S par seconde .</li>
<li>Enregistrez l’heure du pic.</li>
<li>Cliquez sur APM.</li>
<li>Veillez à sélectionner Heure des transactions web dans le filtre déroulant du graphique principal.</li>
<li>Définissez l’heure du pic que vous avez enregistré.</li>
<li>Recherchez les transactions qui ont provoqué des opérations d’E/S élevées.</li>
<li>Explorez chaque trace de transaction &gt; Détails de la trace pour identifier ce qui peut causer des problèmes.</li>
</ol>
</td>
</tr>
<tr>
<td>
<p>Panne : New Relic détermine les pannes par Apdex. Une ligne rouge s’affiche sur le graphique de score Apdex, qui indique Apdex &lt; 0,4, ce qui est considéré comme une panne.</p>
</td>
<td>
<p>L’enquête sur une panne peut prendre plusieurs mesures, notamment l’examen des transactions web et non web, des bases de données et des transactions tierces. Transactions Web :</p>
<ol>
<li>Connectez-vous à <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Aperçu. Vérifiez que le filtre est défini sur l’heure des transactions web dans le filtre graphique déroulant.</li>
<li>Réduisez manuellement la fenêtre temporelle.</li>
<li>Cliquez sur Transactions. Assurez-vous que les filtres sont définis sur Web et sur Les plus longs. Recherchez la transaction la plus longue.</li>
<li>Si vous devez effectuer des recherches plus approfondies, pensez à vérifier les transactions non Web.</li>
</ol>
<p>Transactions non-web :</p>
<ol>
<li>Revenez à la page Aperçu et passez aux Transactions non web dans le filtre déroulant.</li>
<li>Examinez les traces de transaction au tout bas de la page, une par une.</li>
<li>Selon le problème, vous devrez peut-être utiliser un outil tiers comme un profileur PHP pour trouver un goulot d'étranglement.</li>
<li>Si vous avez besoin de plus amples informations, pensez à examiner les processus de base de données.</li>
</ol>
<p>Processus de base de données :</p>
<ol>
<li>Sur la page APM, accédez à Surveillance &gt; Bases de données.</li>
<li>Triez par Les plus chronophages.</li>
<li>Examinez les requêtes TOP.

Remarque : <code>MISE À JOUR</code> ou <code>INSERT</code>les requêtes sont les requêtes qui consomment le plus de CPU.</li>
<li>Basculez sur Débit dans Trier par sélecteur et recherchez les processus qui ont provoqué la liste déroulante du débit de la base de données.</li>
<li>Si vous avez besoin d’approfondir vos connaissances, pensez à examiner les services tiers.</li>
</ol>
<p>Services tiers :</p>
<ol>
<li>Sur la page APM, accédez à Surveillance &gt; Services externes.</li>
<li>Sélectionnez le temps de réponse moyen le plus lent dans la liste déroulante Trier par .</li>
<li>Recherchez les processus qui se sont produits juste avant la panne.</li>
</ol>
</td>
<td>
<p>Pour en savoir plus sur l'examen de problèmes de performances spécifiques, consultez la <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions">Documentation de New Relic &gt; Pages de l'interface utilisateur d'APM &gt; Page des transactions &gt; Utiliser les fonctions d'analyse</a>.</p>
</td>
</tr>
</tbody>
</table>
