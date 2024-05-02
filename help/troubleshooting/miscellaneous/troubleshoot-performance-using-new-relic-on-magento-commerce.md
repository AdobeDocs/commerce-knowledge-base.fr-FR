---
title: Dépannage des performances à l’aide de New Relic sur Adobe Commerce
description: '"Cet article décrit les étapes de dépannage permettant de résoudre les problèmes de performances de l’infrastructure cloud d’Adobe Commerce à l’aide de New Relic. Il fournit également des ressources pour plus d’informations. Voici une liste de problèmes. Cliquez pour afficher les étapes de dépannage dans notre base de connaissances de l’assistance :’'
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---

# Dépannage des performances à l’aide de New Relic sur Adobe Commerce

Cet article décrit les étapes de dépannage permettant de résoudre les problèmes de performances de l’infrastructure cloud d’Adobe Commerce à l’aide de New Relic. Il fournit également des ressources pour plus d’informations. Les problèmes suivants couverts dans le tableau ci-dessous avec les ressources recommandées sont :

* Note d’API basse
* Utilisation élevée du processeur
* Opérations d’E/S élevées
* Désactivation

<table>
<tbody>
<tr>
<td>Problème</td>
<td>Dépannage</td>
<td>Ressources</td>
</tr>
<tr>
<td>
<p>Note Apdex faible :</p>
<p>Votre New Relic <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction">Score d’application</a> mesure la satisfaction des utilisateurs quant au temps de réponse de vos applications et services web.</p>
</td>
<td>
<p>Vous vous connectez à <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Aperçu. Sur le côté droit de la page Aperçu, vous voyez le graphique de score Apdex. Un score Apdex de 0,5 ou moins est un point de préoccupation et mérite une enquête : heures des transactions web (demandes serveur) :</p>
<ol>
<ol>
<li>Connexion à <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (Sélectionner une application) &gt; Aperçu. Assurez-vous que le filtre est défini sur l'heure des transactions Web dans le filtre déroulant du graphique principal. Dans le tableau Transactions ci-dessous, recherchez l’heure du serveur d’applications. Vérifiez si vous avez des transactions de longue date ou suspectes.</li>
<li>Examinez-les individuellement en accédant à Surveillance &gt; Transactions et assurez-vous de définir les filtres pour le Web et le plus chronophage<em>.</em>
</li>
<li>Recherchez ensuite des modules tiers qui consomment des ressources : fournisseurs de paiement, ERP, etc.</li>
<li>Dans la section Surveillance d’APM :<ol>
<li>Cliquez sur Transactions.</li>
<li>Faites défiler l'écran vers le bas, cliquez sur Afficher la table des transactions.</li>
<li>Vous pouvez trier les transactions par <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view">divers paramètres</a> et sautez vers ceux qui causent de la suspicion.</li>
<li>Passez en revue ces transactions avec un score Apdex faible, un nombre exceptionnellement élevé, un temps moyen élevé ou un pourcentage de dissidence.</li>
<li>Cliquez sur chaque transaction. Si vous ne parvenez pas à résoudre le problème, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">soumettez un ticket d’assistance.</a>
</li>
<li>Si vous devez approfondir vos recherches, pensez à vérifier les transactions non-web.</li>
</ol>
</li>
</ol>
</ol>
<p>Durée hors transaction web (opérations et tâches en arrière-plan) :</p>
<ol>
<ol>
<li>Connexion à <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (Sélectionner une application) &gt; Aperçu. Assurez-vous de sélectionner l'heure des transactions non web sur le filtre déroulant du graphique principal. Cliquez sur les transactions individuelles dans la table des transactions. Recherchez des transactions de longue durée ou suspectes. Cela inclut les tâches principales, les tâches cron ou les tâches d’importation/exportation, y compris les tâches tierces.</li>
</ol>
</ol>
</td>
<td>
<p>Pour en savoir plus sur le score New Relic Apdex, voir <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction">Documentation New Relic &gt; Apdex APM &gt; Mesurer la satisfaction des utilisateurs</a>. Vous pouvez également consulter la section <a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md">Alertes gérées pour Adobe Commerce : alerte d’avertissement Apdex</a> dans notre base de connaissances de soutien.</p>
</td>
</tr>
<tr>
<td>
<p>Utilisation élevée du processeur :</p>
<p>Une utilisation élevée du processeur peut indiquer qu’il existe un service particulièrement occupé, comme MySQL, Redis, etc.</p>
</td>
<td>
<ol>
<li>Connexion à <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastructure &gt; Processus.</li>
<li>Consultez les graphiques du processeur pour voir s’il existe un processus bloqué ou à forte consommation qui utilise plus de 100 % du temps du processeur et comparez-le au nombre de processeurs sur l’instance. Faites attention aux pics d’utilisation des ressources. Il n’est pas recommandé de tuer un processus, sauf s’il s’agit d’un cron bloqué.</li>
</ol>
</td>
<td>
<p>Pour en savoir plus sur les mesures de performances, en particulier le pourcentage du processeur, les octets d’E/S et l’utilisation de la mémoire pour des processus individuels ou des groupes, reportez-vous à la section <a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes">Documentation New Relic &gt; Page d’interface utilisateur de l’infrastructure &gt; Page hôte de l’infrastructure &gt; Onglet Processus</a>.</p>
</td>
</tr>
<tr>
<td>
<p>Opérations d’E/S élevées : pour chaque client, ce nombre serait individuel, mais sera sensiblement différent de la moyenne.</p>
</td>
<td>
<p>Recherchez un pic inhabituel par rapport aux opérations d’E/S moyennes précédentes :</p>
<ol>
<li>Connexion à <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastructure &gt; Processus.</li>
<li>Examinez le graphique Lecture d’E/S par seconde.</li>
<li>Enregistrez l’heure du pic.</li>
<li>Cliquez sur APM.</li>
<li>Veillez à sélectionner l’heure des transactions web sur le filtre déroulant du graphique principal.</li>
<li>Définissez l’heure du pic enregistré.</li>
<li>Recherchez les transactions qui ont provoqué des opérations d’E/S élevées.</li>
<li>Explorez chaque trace de transaction &gt; Détails du suivi pour trouver ce qui peut être à l’origine de problèmes.</li>
</ol>
</td>
</tr>
<tr>
<td>
<p>Désactivation : New Relic détermine les pannes par défaut d’Apdex. Une ligne rouge s’affiche sur le graphique de score Apdex, qui indique Apdex &lt; 0.4, ce qui est considéré comme une panne.</p>
</td>
<td>
<p>L’enquête sur une panne peut prendre plusieurs mesures, en examinant les transactions web et non-web, les bases de données et les transactions tierces. Transactions web :</p>
<ol>
<li>Connexion à <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Aperçu. Assurez-vous que le filtre est défini sur la durée des transactions Web sur le filtre de graphique déroulant.</li>
<li>Limitez manuellement la fenêtre temporelle.</li>
<li>Cliquez sur Transactions. Assurez-vous que les filtres sont définis sur Web et prennent le plus de temps. Examinez la transaction la plus longue.</li>
<li>Si vous devez approfondir vos recherches, pensez à vérifier les transactions non-web.</li>
</ol>
<p>Transactions non web :</p>
<ol>
<li>Revenez à la page Aperçu et passez aux transactions non web sur le filtre déroulant.</li>
<li>Vérifiez les traces de transaction tout en bas de la page, une par une.</li>
<li>Selon le problème, vous devrez peut-être utiliser un outil tiers tel qu’un profileur PHP pour trouver un goulot d’étranglement.</li>
<li>Si vous devez approfondir vos recherches, envisagez d’examiner les processus de base de données.</li>
</ol>
<p>Processus de base de données :</p>
<ol>
<li>Sur la page APM, accédez à Surveillance &gt; Bases de données.</li>
<li>Tri selon le plus chronophage.</li>
<li>Examinez les requêtes TOP.

Remarque : <code>UPDATE</code> ou <code>INSERT</code>les requêtes sont les requêtes qui consomment le plus d’unité centrale.</li>
<li>Passez à Débit à partir du sélecteur Trier par et recherchez les processus qui ont provoqué la liste déroulante du débit de la base de données.</li>
<li>Si vous devez approfondir vos recherches, pensez à examiner les services tiers.</li>
</ol>
<p>Services tiers :</p>
<ol>
<li>Sur la page APM, accédez à Surveillance &gt; Services externes.</li>
<li>Sélectionnez le temps de réponse moyen le plus lent dans la liste déroulante Trier par .</li>
<li>Recherchez les processus qui se sont produits juste avant la panne.</li>
</ol>
</td>
<td>
<p>Pour en savoir plus sur les problèmes de performances spécifiques, reportez-vous à la section <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions">Documentation New Relic &gt; Pages de l’interface utilisateur APM &gt; Page des transactions &gt; Utiliser des fonctions d’analyse en profondeur</a>.</p>
</td>
</tr>
</tbody>
</table>
