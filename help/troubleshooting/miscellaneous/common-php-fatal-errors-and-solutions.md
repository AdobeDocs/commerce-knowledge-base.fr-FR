---
title: Erreurs et solutions PHP fatales courantes
description: Cet article répertorie quelques exemples rapides courants d'erreurs fatales PHP que vous pouvez trouver en parcourant vos logs Adobe Commerce et les solutions aux problèmes qu'ils indiquent.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 8be0c125bb0417e34e016656337506da88796630
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Erreurs et solutions PHP fatales courantes

Cet article répertorie quelques exemples rapides courants d&#39;erreurs fatales PHP que vous pouvez trouver en parcourant vos logs Adobe Commerce et les solutions aux problèmes qu&#39;ils indiquent.

## Exemple

Erreur fatale *&#39;PHP : délai d&#39;exécution maximum de 60 secondes dépassé en ....&#39;*

## Solution

Vous pouvez mettre à jour le temps d’exécution maximal en définissant une valeur de `max_execution_time` personnalisée dans votre fichier `php.ini` et en procédant à un redéploiement.

Par exemple :

`max_execution_time = 120`

Consultez l&#39;article [&#x200B; Personnaliser les paramètres php.ini &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/app/php-settings).

## Exemple

Erreur fatale de *&#39;PHP : taille de la mémoire autorisée de 792723456 octets épuisés&#39;* (c&#39;est juste un exemple de taille d&#39;octet.)

## Solution

Personnalisez vos paramètres `php.ini`. Consultez cet article [Personnaliser les paramètres php.ini](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/app/php-settings).

## Exemple

*&#39;Avertissement PHP : inconnu : échec de l&#39;ouverture du flux : aucun fichier ou répertoire de ce type*

## Solution

Veillez à ne pas supprimer les fins de style Windows dans le fichier `php.ini`. Sous Windows, les terminaisons de ligne se terminent par une combinaison d&#39;un retour chariot (ASCII 0x0d ou \r) et d&#39;une nouvelle ligne (\n), également appelée CR/LF.

## Exemple

*&#39;Erreur fatale PHP : PDOException non trouvée : SQLSTATE\[HY000\] \[1040\] Trop de connexions dans*

## Solution

L’espace disque de l’environnement MySQL est insuffisant. Fournissez plus d’espace disque pour l’environnement MySQL.

## Exemple

Erreur fatale *&#39;PHP : Erreur de type non trouvée : valeur renvoyée de Magento&#39;*

## Solution

Vérifiez le répertoire `<root>/tmp`, car il est probablement plein. S’il est plein, fournissez plus d’espace dans le répertoire . Il peut s’agir simplement de déplacer des fichiers vers un autre répertoire ou de les supprimer.

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [Erreurs de paramètres PHP](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Paramètres PHP requis](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/prerequisites/php-settings)
* [Vérification Redis](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection)
* [Configurer Redis](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cache/redis/config-redis)
* [Erreur de limite de mémoire PHP](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Solutions aux problèmes courants - Limite de mémoire](https://developer.adobe.com/commerce/testing/guide/unit/command-line#solutions-to-common-problems)
