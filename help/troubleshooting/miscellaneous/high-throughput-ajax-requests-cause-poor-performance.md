---
title: Les requêtes AJAX à débit élevé entraînent de faibles performances
description: Cet article fournit une solution aux problèmes de performances d’Adobe Commerce On-premise ou d’Adobe Commerce sur les sites d’infrastructure cloud en raison de certaines requêtes à débit élevé qui provoquent une charge et un trafic de serveur importants.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: b6e44e106dcc546949459a79c0f2e49b87e1d376
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Les requêtes AJAX à débit élevé entraînent de faibles performances

Cet article fournit une solution aux problèmes de performances d’Adobe Commerce On-premise ou d’Adobe Commerce sur les sites d’infrastructure cloud en raison de certaines requêtes à débit élevé qui provoquent une charge et un trafic de serveur importants.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

>[!NOTE]
>
>Le problème a été corrigé dans la version 2.3.4 d’Adobe Commerce sur l’infrastructure cloud et dans Adobe Commerce On-Premise.

### Problème

Les performances du site sont faibles en raison du débit élevé des requêtes, telles que les requêtes AJAX critiques.

### Cause

Les requêtes AJAX à haut débit incluent celles liées au contenu privé des clients et clientes.

### Solution

Il existe trois solutions :

* [Mise à niveau vers la version 2.3.4](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version).
* Veillez à ce que les requêtes soient moins lourdes (requêtes de mise en cache ou déplacement vers le contenu privé des clients).
* Réduisez le nombre de requêtes.

<u>Allégement des requêtes (requêtes de mise en cache ou déplacement vers le contenu privé des clients)</u>

Si des requêtes AJAX tierces sont déclenchées sur chaque page, essayez de les mettre en cache ou de les déplacer vers le contenu privé des clients. Le commerçant peut le faire en s’assurant que les requêtes AJAX personnalisées sont appelées à l’aide des méthodes HTTP GET. Cela permettra à Fastly de mettre en cache ces requêtes. Si des requêtes AJAX personnalisées ne doivent pas être mises en cache, elles doivent être restructurées en fonction des fonctionnalités de contenu privé. Pour connaître les étapes, reportez-vous [Contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) dans notre documentation destinée aux développeurs.

<u>Réduction du nombre de requêtes</u>

* Désactivez le panier persistant, car il peut augmenter le nombre de requêtes `customer/section/load`. Suivez les étapes de la section [Chemins d’accès persistants au panier](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/paths/config-reference-general) de notre documentation destinée aux développeurs pour voir si le panier persistant est activé.
* Si vous devez recharger ou invalider du contenu dans `sections.xml` suivez les étapes de la section [Contenu privé : invalider le contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content) de notre documentation destinée aux développeurs et développeuses. Assurez-vous que vous n’utilisez pas directement la méthode `customerData.reload()` dans vos personnalisations.
* Vérifiez les autres requêtes POST AJAX sur la même page. Ouvrez l’outil de développement Google Chrome dans le navigateur Google Chrome. Cliquez sur l’onglet **Réseau** puis sur l’onglet **XHR** pour obtenir la liste de toutes les requêtes AJAX de cette page spécifique. Cliquez ensuite sur chaque requête et, dans le champ Méthode de requête , doit correspondre aux requêtes GET. Remarque : Google Chrome est utilisé à titre d’exemple, et il est possible de le faire dans d’autres navigateurs.
* Vérifiez la fonctionnalité du Gestionnaire de balises Google (GTM) qui est une requête AJAX spécifique. L’utilisateur peut supprimer cet AJAX et refactoriser sa personnalisation avec des fonctionnalités privées afin de réduire le nombre total de requêtes au serveur.
* Vérifiez si la bannière Adobe Commerce est activée mais non utilisée. Vous devrez peut-être [Désactiver la sortie de la bannière Adobe Commerce pour améliorer les performances du site](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26909).

### Lectures connexes

Pour plus d’informations sur le contenu client privé, consultez [Contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) dans notre documentation destinée aux développeurs.
