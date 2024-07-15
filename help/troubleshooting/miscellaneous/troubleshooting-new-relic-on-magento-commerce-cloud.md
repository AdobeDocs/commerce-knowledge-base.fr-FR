---
title: Dépannage de New Relic sur Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit des ressources pour le dépannage de New Relic sur Adobe Commerce sur l’infrastructure cloud.
exl-id: ea763291-5c9b-4575-b2ee-820dbc367743
feature: Cloud, Observability, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Dépannage de New Relic sur Adobe Commerce sur l’infrastructure cloud

Cet article fournit des ressources pour le dépannage de New Relic sur Adobe Commerce sur l’infrastructure cloud.

<table>
<tbody>
<tr>
<td class="wysiwyg-text-align-center"><strong>Problème</strong></td>
<td class="wysiwyg-text-align-center"><strong>Cause</strong></td>
<td class="wysiwyg-text-align-center"><strong>Ressources</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Problèmes d’accès</td>
</tr>
<tr>
<td>
<p><u>Impossible d’afficher les projets dans New Relic.</u></p>
<p>Vous vous connectez à <em>New Relic</em> mais vous ne pouvez pas voir les projets que vous devriez avoir le droit d’afficher/d’accéder.</p>
</td>
<td>
<p>Dans ce cas, un utilisateur administrateur doit vous ajouter au projet.</p>
</td>
<td>
<p><a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html">Accès aux services New Relic</a> dans notre base de connaissances d’assistance.</p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Problèmes de données</td>
</tr>
<tr>
<td>
<p><u>Données manquantes après installation.</u></p>
<p>Utilisez l’ <a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/new-relic-diagnostics">utilitaire de diagnostic New Relic</a> pour tenter d’identifier la cause. Si cela n’aide pas, consultez les solutions spécifiques à l’agent. Les liens vers les articles contenant ces solutions se trouvent dans la colonne de droite.</p>
</td>
<td>
<p>Les données manquantes peuvent avoir des causes différentes. Vous devrez peut-être :</p>
<ul>
<li>Vérifiez que l’agent est installé.</li>
<li>Vérifiez le nom et la clé de licence de votre application.</li>
<li>Redémarrez votre serveur web.</li>
<li>Assurez-vous que votre système respecte les exigences de compatibilité.</li>
<li>Paramètres INI.</li>
</ul>
</td>
<td>
<ul>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#apm-agents">Documentation New Relic &gt; Agents APM &gt; Ne pas voir les données</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#browser-agent">Documentation New Relic &gt; Navigateur New Relic &gt; Données invisibles</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#infrastructure-agents">Documentation New Relic &gt; Infrastructure New Relic &gt; Ne pas voir les données</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#mobile-agents">Documentation New Relic &gt; New Relic Mobile &gt; Ne pas voir les données</a></li>
</ul>
</td>
</tr>
<tr>
<td>
<p><u>Incohérence de l’horodatage des transactions.</u> Vous pouvez avoir du mal à trouver de longues transactions (plus de 5 minutes) à l’aide de l’interface utilisateur de New Relic. Vous pouvez également trouver des transactions affichées en dehors de la période prévue.</p>
</td>
<td>
<p>L’interface utilisateur de New Relic affiche l’heure de fin de la transaction, et non l’heure de début de la transaction.</p>
</td>
<td>
<p>Pour calculer le début de la transaction à l’aide de l’interface utilisateur de New Relic, cochez la durée de la transaction. Soustrayez le montant de la durée de l’horodatage (fin de transaction) fourni par l’interface utilisateur de New Relic.</p>
</td>
</tr>
<tr>
<td>
<p>Les requêtes <u>NerdGraph GraphQL <code>curl</code> utilisant des caractères spéciaux tels que <code>|</code> et <code>%</code> ne fonctionnent pas</u>.</p>
</td>
<td>
<p>La fonction "Copier vers curl" de New Relic dans NerdGraph ne permet pas actuellement de gérer les caractères spéciaux tels que <code>|</code> et <code>%</code>.</p>
</td>
<td>
<p>Utilisez une autre bibliothèque d’API pour résoudre le problème avec des caractères spéciaux. Par exemple, la bibliothèque GraphQLClient pour l’API Graphql sous Python ou Apache.commons par des appels au langage Java. Examinez les bibliothèques clientes sur <a href="https://graphql.org/code/">GraphQL</a>.</p>
</td>
</tr>
<tr>
<td>
<p><u>Problèmes d’affichage des graphiques et des tableaux de bord.</u></p>
</td>
<td>
<p>Résolvez les graphiques manquants en ajoutant des domaines New Relic à la liste autorisée ou en désinstallant l’extension du navigateur à l’origine des problèmes.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/apm/new-relic-apm/troubleshooting/charts-missing-or-do-not-render">Documentation New Relic &gt; Graphiques manquants ou non rendus</a> </p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Problèmes liés aux agents PHP</td>
</tr>
<tr>
<td>
<p><u>L’agent PHP n’affiche pas le nombre d’instances correct.</u></p>
</td>
<td>
<p>Le nombre d’instances peut augmenter en fonction des processus principaux et du débit. Les différences entre les valeurs de serveur peuvent être dues à des processus exécutés sur un serveur, mais pas sur l’autre.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/agents/php-agent/troubleshooting/troubleshoot-php-agent-instance-count">Documentation New Relic &gt; Dépannage du nombre d’instances de l’agent PHP</a> </p>
</td>
</tr>
</tbody>
</table>
