---
title: Erreurs et solutions fatales PHP courantes
description: Cet article répertorie quelques exemples rapides d’erreurs fatales PHP courants que vous pouvez trouver lorsque vous examinez vos journaux Adobe Commerce et les solutions aux problèmes qu’ils indiquent.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Erreurs et solutions fatales PHP courantes

Cet article répertorie quelques exemples rapides d’erreurs fatales PHP courants que vous pouvez trouver lorsque vous examinez vos journaux Adobe Commerce et les solutions aux problèmes qu’ils indiquent.

## Exemple

*&#39;Erreur fatale PHP : délai d’exécution maximal de 60 secondes dépassé en....&#39;*

## Solution

Vous pouvez mettre à jour le temps d’exécution maximal en définissant une `max_execution_time` dans votre `php.ini` et redéploiement.

Par exemple :

`max_execution_time = 120`

Consultez la [Personnalisation des paramètres php.ini](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) article.

## Exemple

*&#39;Erreur fatale PHP : taille de mémoire autorisée de 792723456 octets épuisée&#39;* (Il ne s’agit que d’un exemple de taille d’octet.)

## Solution

Personnalisez votre `php.ini` paramètres. Consultez cette section [Personnalisation des paramètres php.ini](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) article.

## Exemple

*&#39;Avertissement PHP : Inconnu : échec de l’ouverture du flux : aucun fichier ou répertoire de ce type&#39;*

## Solution

Veillez à ne pas supprimer les fins de style Windows dans la variable `php.ini` fichier . Sous Windows, les fins de ligne sont interrompues par une combinaison d’un retour chariot (ASCII 0x0d ou \r) et d’une nouvelle ligne (\n), également appelée CR/LF.

## Exemple

*&#39;Erreur fatale PHP : PDOException non interceptée : SQLSTATE\[HY00\] \[1040\] Trop de connexions dans&#39;*

## Solution

L’environnement MySQL n’a plus d’espace disque. Fournissez davantage d’espace disque pour l’environnement MySQL.

## Exemple

*&#39;Erreur fatale PHP : TypeError non intercepté : valeur renvoyée au Magento&#39;*

## Solution

Vérifiez les `<root>/tmp` car il est probablement plein. S’il est plein, indiquez plus d’espace dans le répertoire. Cela peut simplement impliquer le déplacement de fichiers vers un autre répertoire ou leur suppression.

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [erreurs de paramètres PHP](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html)
* [Paramètres PHP requis](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)
* [Redis vérification](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)
* [Configuration de Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)
* [Erreur de limite de mémoire PHP](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html#trouble-php-memory)
* [Solutions aux problèmes courants - Limite de mémoire](https://devdocs.magento.com/guides/v2.3/test/unit/unit_test_execution_cli.html#solutions-to-common-problems)
