---
title: Les demandes d’AJAX à débit élevé provoquent des performances médiocres
description: Cet article fournit une solution pour les problèmes de performances avec Adobe Commerce sur site ou Adobe Commerce sur les sites d’infrastructure cloud en raison de certaines demandes de débit élevé qui provoquent une charge et un trafic de serveur importants.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Les demandes d’AJAX à débit élevé provoquent des performances médiocres

Cet article fournit une solution pour les problèmes de performances avec Adobe Commerce sur site ou Adobe Commerce sur les sites d’infrastructure cloud en raison de certaines demandes de débit élevé qui provoquent une charge et un trafic de serveur importants.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

>[!NOTE]
>
>Le problème a été corrigé dans la version 2.3.4 d’Adobe Commerce sur l’infrastructure cloud et d’Adobe Commerce sur site.

### Problème

Les performances du site sont lentes en raison de requêtes de débit élevé, comme les requêtes d’AJAX critiques.

### Cause

Les demandes d’AJAX à débit élevé incluent celles liées au contenu privé des clients.

### Solution

Il existe trois solutions :

* [Mise à niveau vers la version 2.3.4](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version). Si ce n&#39;est pas possible actuellement, [installez le correctif qui corrige le problème](/help/troubleshooting/known-issues-patches-attached/performance-issues-caused-by-excessive-ajax-requests.md).
* Veillez à des requêtes plus légères (requêtes de cache ou déplacement vers le contenu privé des clients).
* Réduire le nombre de requêtes.

<u>Veillez à des requêtes plus légères (requêtes de cache ou déplacement vers le contenu privé des clients)</u>

Si des demandes d’AJAX tierces sont déclenchées sur chaque page, essayez de mettre en cache ces demandes ou de les déplacer vers le contenu privé des clients. Le commerçant peut le faire en s’assurant que les demandes d’AJAX personnalisées sont appelées à l’aide des méthodes HTTP GET. Ces demandes seront mises en cache rapidement. Si des demandes d’AJAX personnalisées ne doivent pas être mises en cache, elles doivent être refactorisées en fonction de la fonctionnalité de contenu privé. Pour obtenir les étapes nécessaires, reportez-vous à la section [Contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) de notre documentation destinée aux développeurs.

<u>Réduction du nombre de requêtes</u>

* Désactivez le panier persistant, car il peut augmenter le nombre de demandes `customer/section/load`. Suivez les étapes de la section [Chemins du panier persistant](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/paths/config-reference-general) de notre documentation destinée aux développeurs pour savoir si le panier persistant est activé.
* Si vous devez recharger ou invalider du contenu dans `sections.xml`, suivez les étapes de la section [Contenu privé : invalider le contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content) de la documentation destinée aux développeurs. Veillez à ne pas utiliser la méthode `customerData.reload()` directement dans vos personnalisations.
* Cochez d’autres requêtes d’AJAX POST sur la même page. Ouvrez l’outil de développement Google Chrome dans le navigateur Google Chrome. Cliquez sur l’onglet **Réseau** , puis sur l’onglet **XHR** et vous trouverez la liste de toutes les demandes d’AJAX provenant d’une page spécifique. Cliquez ensuite sur chaque requête. Dans le champ Méthode de requête , les requêtes de GET doivent être définies. Remarque : Google Chrome est utilisé comme exemple et il est possible de le faire dans d’autres navigateurs également.
* Cochez la fonctionnalité Gestionnaire de balises de Google (GTM) qui est une requête d’AJAX spécifique. L’utilisateur peut supprimer cette AJAX et refactoriser sa personnalisation avec des fonctionnalités privées afin de réduire le nombre total de requêtes envoyées au serveur.
* Vérifiez si la bannière Adobe Commerce est activée, mais pas utilisée. Vous devrez peut-être [désactiver la sortie de la bannière Adobe Commerce pour améliorer les performances du site](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md).

### Lecture connexe

Pour plus d’informations sur le contenu client privé, consultez le [contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) dans notre documentation destinée aux développeurs.
