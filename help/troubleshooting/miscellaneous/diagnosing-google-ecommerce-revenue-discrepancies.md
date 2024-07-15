---
title: Diagnostic des incohérences entre les recettes de Google eCommerce
description: '"Cet article fournit des solutions aux incohérences entre Google et Magento Business Intelligence (MBI). Le suivi de Google eCommerce optimise votre compte de Google Analytics et vos tableaux de bord de MBI, mais de nombreux clients nous demandent si les deux outils doivent signaler le même montant de **commandes** et **recettes**?.'
exl-id: b2e43e70-d234-4338-ae81-fa401416be5a
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 0%

---

# Diagnostic des incohérences entre les recettes de Google eCommerce

Cet article fournit des solutions aux incohérences entre Google et Magento Business Intelligence (MBI). Le suivi de Google eCommerce optimise votre compte de Google Analytics et vos tableaux de bord MBI, mais de nombreux clients nous demandent : les deux outils doivent-ils générer le même volume de **commandes** et de **recettes** ?

D&#39;après notre expérience, la réponse est &quot;non&quot; dans presque tous les cas. En effet, le suivi de Google eCommerce obtient les informations de commande lors d’un événement de clic sur un bouton sur votre site web, ce qui omet de nombreux attributs de commande enregistrés plus tard dans votre base de données, depuis les commandes non enregistrées jusqu’à celles annulées ou remboursées ultérieurement.

Nous savons qu’une incohérence entre Google et l’IMS peut provoquer une incertitude pour vous et votre équipe. Nous voulons vous aider à comprendre la différence entre ces deux nombres, ce qui peut révéler des ajustements à effectuer dans votre compte ou votre base de données Google.

## Pourquoi la disponibilité générale signale-t-elle **moins** de recettes par rapport à ma base de données ?

Lorsque les Google Analytics sous-évaluent les commandes et les recettes, cela indique qu’ils ne capturent pas toutes les commandes effectuées sur votre site. Puisque vous savez que les données de votre base de données sont le nombre définitif, vous pouvez prendre quelques mesures pour déterminer la cause première et peut éventuellement aider Google à capturer plus d’informations.

* Le suivi du commerce électronique Google n’était pas toujours activé sur votre compte. Essayez d’observer une période plus petite et plus récente.
* Votre suivi Google eCommerce n’est pas configuré pour capturer les achats de certains navigateurs, systèmes d’exploitation ou périphériques.
* L’événement click associé à votre suivi Google eCommerce ne suit pas correctement les taxes, les frais de livraison ou d’autres frais au-dessus du total de la commande.
* L’horodatage de votre base de données se trouve dans un fuseau horaire différent de celui de vos Google Analytics.
* Les visiteurs peuvent se rendre sur votre site par le biais de fenêtres incognito ou en désactivant les cookies.

## Pourquoi la disponibilité générale signale-t-elle **plus** de recettes par rapport à ma base de données ?

Nous avons constaté qu’il est plus courant pour les Google Analytics de sursignaler les commandes et les recettes par rapport à une base de données eCommerce. Ce n&#39;est pas toujours une mauvaise chose. Votre base de données est l’enregistrement définitif des transactions effectuées sur votre site web. Il existe plusieurs raisons pour lesquelles Google peut générer des rapports importants même si vous l’avez parfaitement configurée :

* Le suivi eCommerce capture les clics sur les boutons en double en ne s’enregistrant que dans une seule commande de votre base de données.
* Vous avez un grand nombre de commandes annulées, remboursées ou frauduleuses, ce qui correspond à un changement d’état qui se produit une fois que eCommerce a suivi les données.
* Vos mesures **Recettes** et **Commandes** excluent délibérément les commandes de test ou internes, que Google ne peut pas différencier.
* Dans certains cas, le placement de commandes dans votre base de données échoue.
* Le suivi de Google eCommerce ne connaît pas les coupons et les remises sur la commande.
* L’horodatage de votre base de données se trouve dans un fuseau horaire différent de celui de vos Google Analytics.

Souvenez-vous que même si Google signale un nombre plus élevé que votre base de données, il est probable qu’il manque encore certaines commandes pour les raisons présentées dans la section ci-dessus.

## Dépannage

* Créez un clone de votre mesure **Recettes** sans filtres pour limiter le résultat. Les filtres Commandes que nous comptabilisons ou Clients que nous comptons sont importants, mais Google n’a pas de filtre équivalent.
* Effectuez un audit sur une petite période récente, comme une période de quelques heures plus tôt cette semaine.
* Une fois que le suivi Google eCommerce est configuré dans l’IMS, utilisez Filtre ou Groupe-Par pour contrôler une seule Source, Medium ou Campaign. Faites ensuite de même dans Google. Une source avec moins de trafic/recettes sera meilleure, car c’est comme avoir moins de marge d’erreur.
