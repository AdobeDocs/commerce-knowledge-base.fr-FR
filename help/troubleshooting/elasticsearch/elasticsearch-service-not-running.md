---
title: Service Elasticsearch non en cours d’exécution
description: Cet article fournit des solutions aux erreurs que vous pouvez rencontrer lorsque le service Elasticsearch (ES) n’est pas en cours d’exécution (généralement en raison d’un blocage). Les symptômes peuvent inclure des erreurs lors de l’exécution des contrôles de l’intégrité à l’aide de curl, de la réindexation à l’aide de la ligne de commande, des erreurs Exception et PHP, ainsi que des erreurs sur les pages du produit. Le tableau répertorie les erreurs et les liens vers les ressources pour tenter de les résoudre. Un symptôme peut avoir différentes causes.
exl-id: 2c2230de-cb30-4a03-8c3e-d9f44783dbae
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Service Elasticsearch non en cours d’exécution

Cet article fournit des solutions aux erreurs que vous pouvez rencontrer lorsque le service Elasticsearch (ES) n’est pas en cours d’exécution (généralement en raison d’un blocage). Les symptômes peuvent inclure des erreurs lors de l’exécution des contrôles de l’intégrité à l’aide de curl, de la réindexation à l’aide de la ligne de commande, des erreurs Exception et PHP, ainsi que des erreurs sur les pages du produit. Le tableau répertorie les erreurs et les liens vers les ressources pour tenter de les résoudre. Un symptôme peut avoir différentes causes.

## Compatibilité des versions Elasticsearch avec Adobe Commerce

* Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud :

   * v2.2.3+ prend en charge ES 5.x
   * Prise en charge de ES 6.x par v2.2.8+ et v2.3.1+
   * ES v2.x et v5.x ne sont pas recommandés en raison de la [fin de vie](https://www.elastic.co/support/eol). Cependant, si vous disposez d’Adobe Commerce v2.3.1 et que vous souhaitez utiliser ES 2.x ou ES 5.x, vous devez [Changer le client php Elasticsearch](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/search/overview-search).

* Magento Open Source v2.3.0+ prend en charge ES 5.x et 6.x (mais la version 6.x est recommandée).

<table>
<tr>
<th>Symptômes lorsque le service ES ne fonctionne pas</th>
<th>Détails</th>
<th>Ressources</th>
</tr>
<tr>
<td rowspan="3">Erreurs d’exception</td>
</tr>
<tr>
<td>
<code>&lbrace;"0":"&lbrace;\"error\":&lbrace;\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}&rbrack;</code>
</td>
<td>
<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsearch-5-is-configured-but-search-page-does-not-load-with-fielddata-is-disabled...-error.html?lang=fr">Elasticsearch 5 est configuré, mais la page de recherche ne se charge pas avec "Field data is disabled..." erreur</a> dans notre base de connaissances de support.
</td>
</tr>
<tr>
<td>
<code>Elasticsearch\Common\Exceptions\NoNodesAvailableException: Noticed exception 'Elasticsearch\Common\Exceptions\NoNodesAvailableException' with message 'No alive nodes found in your cluster' in /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/ConnectionPool/StaticNoPingConnectionPool.php:51</code>
</td>
<td>
Les index Elasticsuite ne sont pas supprimés.  Voir <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html?lang=fr">Les index de suivi ElasticSuite entraînent des problèmes avec Elasticsearch</a> dans notre base de connaissances de prise en charge.
 </td>
</tr>
<tr>
<td>erreur PHP</td>
<td>
<i>Aucun noeud vivant trouvé dans votre grappe","1":"#0 /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/Transport.php</i>
</td>
<td rowspan="4">
<ul>
<li>Ressources pour un espace disque insuffisant :<ul>
<li><a href="https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/">8 conseils pour résoudre les problèmes de disque dur des systèmes Linux et Unix tels que Disque complet ou Impossible d’écrire sur le disque</a></li>
<li><a href="https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not">serverfault : df indique que le disque est saturé, mais qu’il ne l’est pas.</a></li>
<li><a href="https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux">unix.stackexchange.com : Suivi de l’emplacement de l’espace disque sous Linux ?</a></li>
<li>Les fichiers journaux ne sont pas suffisamment archivés régulièrement. Voir <a href="https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/action-logs/action-log-archive">Configuration de l’archive de journaux</a> dans notre documentation destinée aux développeurs.</li>
<li>Les répertoires système de fichiers ne sont pas optimisés. Voir <a href="https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/tools/developer-tools#resource-file-optimization">Optimisation de fichier</a> dans notre documentation destinée aux développeurs.</li>
<li>Si les solutions présentées dans la documentation ci-dessus ne résolvent pas le problème, contactez votre équipe de compte d’Adobe pour demander un stockage supplémentaire.</li>
</ul>
</li>
<li>Si votre disque n’est pas saturé de stockage, mais que vous recevez toujours les messages d’erreur dans la colonne de gauche, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket"> envoyez un ticket d’assistance</a>.</li>
</ul>
<ul>
<li>Voir <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html?lang=fr">Les index de suivi ElasticSuite entraînent des problèmes avec Elasticsearch</a> dans notre base de connaissances de prise en charge.
</li>
</ul>
</td>
</tr>
<tr>
<td><code>Curl</code> error</td>
<td>L’exécution de la commande <code>curl</code> pour vérifier l’intégrité de l’Elasticsearch : <code>curl -m1 localhost:9200/_cluster/health?pretty</code> (ou <code>curl -m1 elasticsearch.internal:9200/_cluster/health?pretty</code> pour les comptes Starter) génère l’erreur suivante : <i>Erreur : curl : (7) Échec de la connexion au port localhost 9200 : connexion refusée</i> </td>
</tr>
<tr>
<td>Erreur de ligne de commande</td>
<td>L'exécution de <code>$ bin/magento indexer:reindex catalogsearch_fulltext</code> génère cette erreur <i>Le processus d'indexation de la recherche catalogue effectue une erreur inconnue :
        Aucun noeud actif trouvé dans votre grappe</i>
</td>
</tr>
<tr>
<td>Erreur sur les pages de produits
</td>
<td><i>Une erreur s’est produite lors du traitement de votre requête.
      L’impression d’exception est désactivée par défaut pour des raisons de sécurité.</code></i>
</tr>
</table>
