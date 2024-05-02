---
title: Utilisation des exportations de données pour identifier les disparités
description: Cet article fournit des solutions pour résoudre les problèmes liés aux incohérences entre les données de la BI du Magento. Les exportations de données constituent un outil utile pour comparer vos données de BI Magento à vos données source afin de mettre en évidence les incohérences de données dans vos rapports, en particulier si la [liste de contrôle de diagnostic de l’incohérence de données](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md) ne vous a pas aidé à identifier le problème. Cet article vous présente un exemple concret de la manière dont les écarts de données peuvent être identifiés à l’aide des exportations de données.
exl-id: b42d585c-ad8c-4685-9ad4-a13686566f18
feature: Commerce Intelligence, Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 0%

---

# Utilisation des exportations de données pour identifier les disparités

Cet article fournit des solutions pour résoudre les problèmes liés aux incohérences entre les données de la BI du Magento. Les exportations de données constituent un outil utile pour comparer vos données de BI Magento à vos données source afin de mettre en évidence les incohérences entre les données dans vos rapports, en particulier si la variable [liste de contrôle de diagnostic d’incohérence des données](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md) ne vous a pas aidé à déterminer le problème. Cet article vous présente un exemple concret de la manière dont les écarts de données peuvent être identifiés à l’aide des exportations de données.

Prenez cette analyse, par exemple :

![](assets/Exports_Discrepancies_1.png)

Il y a une baisse suspecte en novembre 2014. 500 780,94 $ en recettes ? Ça ne semble pas correct. Vous avez confirmé que d’autres recettes s’affichent pour le mois de novembre 2014 dans votre base de données source, et vous avez vérifié que la variable **Recettes** La mesure utilisée dans ce rapport est correctement définie. Il semble que les données de l’entrepôt de données Magento BI soient incomplètes et peuvent être confirmées à l’aide d’une exportation de données.

## Exporter les données {#export}

Pour commencer, cliquez sur l’engrenage dans le coin supérieur droit du graphique, puis sur l’option Exportation brute dans le menu déroulant. Vous obtiendrez ainsi une exportation brute des données derrière le graphique.

![](assets/Export_Discrepancies_5.gif)

Dans le menu Exportation des données brutes, vous pouvez sélectionner le tableau à exporter avec les colonnes à inclure dans l’exportation. Les filtres peuvent également être appliqués au jeu de résultats.

Dans notre exemple, la variable **Recettes** La mesure utilisée sur ce rapport utilise la variable **order\_total** champ défini sur le champ **commandes** , à l’aide de la variable **date** comme horodatage. Dans notre export, nous voulons inclure tous les **order\_id** pour novembre 2014 et leurs **order\_total** . La variable **Recettes** n’utilise aucun filtre, mais nous ajouterons un filtre à l’exportation pour limiter le jeu de résultats à novembre 2014.

Voici à quoi ressemble le menu Exportation de données brutes pour cet exemple :

![](assets/Exports_Discrepancies_2.png)

Cliquez sur Exporter les données pour lancer l’exportation. Une fenêtre contenant les détails de l&#39;export, y compris le statut, s&#39;affiche. La préparation de l&#39;export prend quelques minutes, ce qui donne à présent un bon moment pour réaliser un extrait analogue de nos données sources pour novembre 2014, y compris : **date, order\_id** , et la variable **order\_total** . Nous allons ouvrir ce fichier dans Excel et le laisser tel quel, comme nous y reviendrons bientôt.

Lorsque le bouton Télécharger s’affiche dans la fenêtre Exports de données brutes, cliquez dessus pour télécharger le fichier zip contenant le fichier CSV.

![](assets/Export_Discrepancies_6.png)

A ce stade, nous devons rassembler toutes les données dans une feuille pour trouver le problème. Nous allons importer le fichier CSV (exportation à partir de Magento BI) dans une autre feuille du fichier Excel contenant nos données source.

## Identifier le problème {#pinpoint}

Maintenant que toutes les données sont à un seul endroit, nous pouvons chercher la source de l&#39;incohérence. La comparaison du nombre de lignes dans chaque feuille nous aidera à déterminer le problème. Regardons de plus près chaque situation.

### Les deux feuilles contiennent le même nombre de lignes

Si les deux systèmes ont le même nombre de lignes et que la variable **Recettes** La mesure ne correspond pas aux données source, puis la variable **order\_total** Je dois être en déplacement quelque part. Il est possible que la variable **order\_total** a été mis à jour dans votre base de données source et Magento BI ne récupère pas ces modifications.

Pour confirmer cela, vérifiez si la variable **order\_total** est en cours de réactivation. Accédez au Gestionnaire de Data Warehouse et cliquez sur la table des commandes. Vous verrez le [fréquence de vérification](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html) répertorié dans &quot;Modifications ?&quot; colonne . La variable **order\_total** doit être défini pour vérifier autant de fois qu’il est prévu qu’il change. Dans le cas contraire, continuez et définissez-le sur la fréquence de vérification souhaitée.

### ![](assets/Export_Discrepancies_4.gif)

Si la fréquence de nouveau contrôle est déjà définie correctement, alors quelque chose d&#39;autre ne va pas. Voir [Contacter l’assistance](#support) à la fin de cet article pour les étapes suivantes.

## La base de données source contient PLUS de lignes que Magento BI {#morerows}

Si la base de données source contient plus de lignes que Magento BI et que l’écart est supérieur au nombre de commandes que vous pouvez vous attendre à recevoir pendant la durée d’un cycle de mise à jour, un problème de connexion peut se produire. Cela signifie que Magento BI ne peut pas extraire de nouvelles données de la base de données source, ce qui peut se produire pour plusieurs raisons.

Accédez à la page Connexions et examinez l’état de la source de données contenant le tableau de commande :

1. **Si l’état est Re-auth** , la connexion n’utilise pas les informations d’identification correctes. Cliquez sur la connexion, saisissez les informations d’identification correctes, puis réessayez.
1. **Si l’état est En échec** , la connexion peut ne pas être configurée correctement du côté serveur. Les connexions en échec proviennent généralement d’un nom d’hôte incorrect ou du serveur cible qui n’accepte pas les connexions sur le port spécifié. Cliquez sur dans la connexion et vérifiez l’orthographe du nom d’hôte et que le port correct est saisi. Côté serveur, assurez-vous que le port peut accepter les connexions et que votre pare-feu dispose de l’adresse IP Magento BI (54.88.76.97/32) comme autorisé. **Si la connexion continue à échouer** , reportez-vous au [Contacter l’assistance](#support) à la fin de cet article pour les étapes suivantes.
1. **Si l’état a réussi** , alors la connexion n&#39;est pas le problème et le support RJ doit être impliqué. Voir [Contacter l’assistance](#support) à la fin de cet article pour les étapes suivantes.

## La base de données source contient MOINS de lignes que Magento BI {#lessrows}

Si la base de données source contient moins de lignes que Magento BI, il est possible que les lignes soient supprimées de la base de données source et que Magento BI ne sélectionne pas ces suppressions. ** [Suppression de données](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) peut entraîner des incohérences, des temps de mise à jour plus longs et une foule de maux de tête logistiques** . Nous vous recommandons donc vivement de ne jamais supprimer de données à moins qu’elles ne soient vraiment nécessaires.

Toutefois, si des lignes sont supprimées du tableau, observez la fréquence de vérification sur la clé primaire. Le nouveau contrôle de la clé primaire permet de rechercher les lignes supprimées dans la table.

Dans le Gestionnaire de Data Warehouse, les colonnes de clé primaire sont marquées d’un symbole de clé. Dans notre exemple, la clé primaire est la clé **order\_id** column :

![](assets/Export_Discrepancies_3.png)

Si la clé primaire est déjà paramétrée pour être vérifiée ou si les lignes ne sont jamais supprimées de cette table, vous aurez besoin de la prise en charge de RJ pour identifier le problème. Reportez-vous à la section suivante pour connaître les étapes suivantes.

## Contacter l’assistance {#support}

Si vous ne parvenez pas à déterminer la source du problème, vous devrez effectuer une boucle dans le support RJ. Avant d’envoyer un ticket, procédez comme suit :

* **Si votre base de données source et votre Magento BI ont le même nombre de lignes** et vérifiez que les fréquences sont correctement définies. Exécutez un VLOOKUP dans votre feuille de calcul. **pour déterminer quelles valeurs order\_id ont une valeur order\_total différente entre Magento BI et votre base de données source.** Incluez ces valeurs lorsque vous envoyez votre ticket.
* **Si votre base de données source contient PLUS de lignes que Magento BI** et que la connexion s’affiche comme ayant réussi ou continue à échouer, nous devrons connaître le nom de la connexion et le message d’erreur que vous voyez, s’il y en a un.
* **Si votre base de données source contient MOINS de lignes que Magento BI,** les lignes ne sont pas supprimées de la table et les fréquences de nouveau-contrôle sont correctement définies, effectuez une VLOOKUP dans votre feuille de calcul. **pour trouver les valeurs order\_id dans Magento BI** mais pas dans votre base de données source. Incluez ces valeurs lorsque vous envoyez votre ticket.

## Associé

* [Liste de contrôle de diagnostic des incohérences de données](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md)
* [Envoi d’un ticket d’incohérence de données](https://support.magento.com/hc/en-us/articles/360016506472-Submitting-a-data-discrepancy-ticket)
