---
title: 'Requêtes SQL : erreurs de coût EXPLAIN'
description: Cet article fournit des solutions pour les erreurs de coût EXPLAIN lors de l’exécution de requêtes SQL infructueuses. PostgreSQL utilise ce qu'on appelle [la commande EXPLAIN](https://www.postgresql.org/docs/9.5/static/using-explain.html) pour déterminer le coût des requêtes SQL. Nous avons créé le Report Builder SQL pour utiliser également cette commande, ce qui signifie que si le coût est jugé trop élevé - la quantité de ressources requises pour exécuter la requête dépasse les seuils - la requête ne s’exécute pas et un message EXPLAIN s’affiche.
exl-id: 6f6df66a-665e-46a8-ad4c-842a0270c4eb
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Requêtes SQL : erreurs de coût EXPLAIN

Cet article fournit des solutions pour les erreurs de coût EXPLAIN lors de l’exécution de requêtes SQL infructueuses. PostgreSQL utilise quelque chose appelé [la commande EXPLAIN](https://www.postgresql.org/docs/9.5/static/using-explain.html) pour déterminer le coût des requêtes SQL. Nous avons créé le Report Builder SQL pour utiliser également cette commande, ce qui signifie que si le coût est jugé trop élevé - la quantité de ressources requises pour exécuter la requête dépasse les seuils - la requête ne s’exécute pas et un message EXPLAIN s’affiche.

Il y a quelques raisons à cela. Voici les messages que vous pourriez recevoir, ce qu’ils veulent dire et comment les résoudre.

## Impossible d’exécuter la requête. La valeur de coût EXPLAIN de \[xxx\] est trop élevée pour exécuter cette requête.

Si ce message s’affiche, cela signifie que la requête a été jugée trop coûteuse à exécuter. Nous avons deux recommandations pour cette situation : l’une consiste à éliminer toute clause ORDER BY de votre requête, car il s’agit d’opérations coûteuses. La seconde consiste à suivre les conseils de notre [article sur l&#39;optimisation](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/optimizing-your-sql-queries.html?lang=fr) pour ajuster votre requête.

## Impossible d’exécuter la requête. Cette requête renvoie \[xxx\] lignes qui dépassent notre limite de 10 000.

Dans ce cas, le nombre de résultats possibles dépasse le nombre maximal défini pour le Report Builder SQL. Il existe plusieurs façons de réduire le nombre de résultats :

* Essayez d’ajouter des filtres à votre requête.
* Utilisez LIMIT, si possible. Certains tableaux comportent un grand nombre de lignes et la limitation des résultats peut vous maintenir sous la limite des lignes.

## Impossible d’analyser la réponse EXPLAIN.

Oups. Ce message signifie généralement que quelque chose a probablement mal tourné de notre côté. Si vous continuez à recevoir cette erreur, contactez l’assistance.
