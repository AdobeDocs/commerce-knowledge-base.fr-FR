---
title: Site cloud lent
description: Cet article fournit des recommandations sur la manière de rendre votre site Adobe Commerce sur l’infrastructure cloud plus performant en cas de forte charge de trafic et sur la manière de réduire cette charge.
exl-id: 144df36b-6305-4e57-b813-46bbb0ddedda
feature: Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---

# Site cloud lent

Cet article fournit des recommandations sur la manière de rendre votre site Adobe Commerce sur l’infrastructure cloud plus performant en cas de forte charge de trafic et sur la manière de réduire cette charge.

## Versions et éditions affectées

* Adobe Commerce sur les infrastructures cloud, toutes versions confondues

## Problème

<u>Procédure à suivre</u>

1. Rendez-vous dans votre boutique Adobe Commerce.
1. Parcourir une page de catégorie.
1. Ajoutez un produit au panier.

<u>Résultat attendu</u>

Le site est réactif et l’ajout d’un produit au panier est rapide.

<u>Résultat réel</u>

Le site est lent ou les pages de catégories sont rapides, mais la page du panier est lente.

## Étapes et solutions de débogage

Suivez les étapes suivantes pour déterminer la raison de la lenteur des performances et y remédier. Vous pouvez passer aux première et deuxième étapes, mais ne passez au blocage des adresses IP que si l’optimisation des paramètres du cache ne vous aide pas.

1. Vérifiez le taux d’accès au cache pour les pages avec un trafic élevé et réduisez la quantité de données fortement mises à jour.
1. Vérifiez le taux d’accès global au cache du site et la configuration générale du cache/Fastly.
1. Identifiez les clients web à l’origine de la charge élevée du serveur et bloquez les adresses IP à l’origine de la charge élevée.

Les paragraphes suivants fournissent plus de détails sur chaque étape.

### Étape 1 : vérifier le taux d’accès au cache pour les pages avec un trafic élevé

La première étape pour résoudre un site encombré par un trafic important consiste à s’assurer que les pages ayant le trafic le plus important, comme la page d’accueil du magasin et les pages de catégorie supérieure, sont correctement mises en cache.

Vous pouvez connaître les taux d’accès au cache de ces pages en consultant les en-têtes HTTP `X-Cache` à l’aide de cURL, comme décrit dans la section [Vérification du cache à l’aide de cURL](https://docs.fastly.com/guides/debugging/checking-cache#using-curl) dans la documentation Fastly . Vous pouvez également vérifier les mêmes en-têtes à l’aide de l’onglet réseau de la barre d’outils de développement de votre navigateur web préféré.

Fastly respecte généralement les en-têtes de réponse provenant de l’application ; cependant, si les en-têtes sont tous définis sur « ne pas mettre en cache » et que la page « expire dans le passé », Fastly ne peut pas mettre la page en cache.

>[!WARNING]
>
>Notez que Fastly modifie les en-têtes de réponse. Par conséquent, vérifier l’URL principale avec cURL ou le navigateur web n’affichera pas nécessairement les en-têtes émis par l’application. Il est courant que Fastly lui-même réponde aux navigateurs web avec des en-têtes « sans cache », mais que l’application web elle-même autorise la mise en cache et que Fastly mette correctement en cache l’élément. Les informations d’en-têtes « cache-control » et « pragma » ne seront donc pas utiles dans ce cas.

#### Dépannage des pages à trafic élevé

Si le taux d’accès à la page d’index est faible, vous pouvez le corriger en réduisant la quantité de données fortement mises à jour présentes sur cette page.

### Étape 2 : vérifier le taux d’accès global au cache du site

Pour vérifier le taux d’accès global au cache :

1. [Obtenez des informations d’identification Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration) pour votre environnement Adobe Commerce sur infrastructure cloud.
1. Exécutez la commande cURL Linux/macOS suivante pour vérifier le taux d’accès à votre site au cours des 30 dernières minutes, en remplaçant et par les valeurs de vos informations d’identification Fastly :

   `curl -H "Fastly-Key: " https://api.fastly.com/stats/service//field/hit_ratio?by=minute | json_pp`

   Vous pouvez également vérifier les taux d’accès historiques au cours du dernier jour ou mois en modifiant l’option de requête de période de `?by=minute` à `?by=hour` ou `?by=day`. Pour plus d’informations sur l’obtention des statistiques de cache Fastly, voir [Options de requête](https://docs.fastly.com/api/stats#Query) dans la documentation Fastly.

   L’option `| json_pp` imprime pratiquement la sortie de la réponse JSON à l’aide de l’utilitaire `json_pp`. Si vous obtenez l’erreur « a_&#39;json\_pp not found », installez l’utilitaire `json_pp` ou utilisez un autre outil de ligne de commande pour l’impression JSON pretty. Vous pouvez également supprimer le paramètre `| json_pp` et exécuter à nouveau la commande . La sortie de réponse JSON n’est pas formatée, mais vous pouvez l’exécuter via un embellisseur JSON pour la nettoyer.

Un taux d’accès supérieur à 0,90 ou 90 % indique que le cache de pleine page fonctionne.

Un taux d’accès inférieur à 0,85 ou 85 % peut indiquer un problème de configuration du site, ou il se peut que vous ayez installé une extension tierce qui ne permet pas la mise en cache de son contenu.

#### Dépannage du taux d’accès global au cache

1. À l’aide des statistiques de taux d’accès horaire et quotidien, déterminez à quel moment le taux d’accès a commencé à diminuer. Si le taux d’accès baisse soudainement au moment où vous déployez une modification sur votre site, envisagez de restaurer la modification jusqu’à ce que le chargement du site diminue.
1. Vérifiez la configuration dans l’administration Commerce, sous **Magasins** > **Configuration** > Avancé > **Système** > **Cache de page complet**. Assurez-vous que la valeur **TTL pour le contenu public** n’est pas définie sur une valeur trop basse.
1. Vérifiez que vous avez [téléchargé les fragments de code VCL](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
1. Si vous utilisez des fragments de code VCL personnalisés, déboguez-les pour une utilisation correcte des actions « pass » ou « pipe » : ils doivent être utilisés avec précaution et au minimum utilisés avec une condition d&#39;un certain type. Pour plus de conseils, consultez [Fragments de code VCL Fastly personnalisés](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) dans notre documentation destinée aux développeurs.

### Étape 3 : identifier les sites web à l’origine de la charge élevée du serveur

Vous pouvez utiliser l’une des méthodes suivantes pour obtenir des informations sur les adresses IP qui accèdent à votre boutique Adobe Commerce.

* Vérifiez les journaux d’accès HTTP via une session SSH.
* Contactez l’assistance Adobe Commerce pour demander une liste d’adresses IP à l’origine d’une charge importante sur le site.

#### Vérifier les journaux d’accès HTTP

Pour afficher le journal des accès de votre site, exécutez la commande suivante à partir de votre environnement de développement local :

```bash
magento-cloud log access
```

Afficher plus de lignes avec le

```bash
--lines
```

, par exemple :

```bash
magento-cloud log access --lines=500
```

Vous pouvez afficher ce journal et vérifier si une grande partie des requêtes provient d’une adresse IP spécifique. Vous pouvez également utiliser `awk` , `sort` et `uniq` pour compter automatiquement les adresses IP les plus courantes dans le journal, comme suit :

```bash
magento-cloud log access --lines 2000 | awk '{print $1}' | sort | uniq -c | sort
  -nr
```

Si le

```bash
magento-cloud log
```

La commande ne fonctionne pas. Vous pouvez vous connecter au serveur distant avec SSH et vérifier le fichier journal à `/var/log/access.log`

Après avoir identifié les adresses IP qui provoquent une charge importante du serveur, vous pouvez les bloquer en configurant une liste bloquée IP à partir du panneau d’administration de Commerce, sous **Magasins** > **Configuration** > AVANCÉ > **Système** > **Cache de page complète** > **Configuration Fastly** > **Blocking**.

Si vous ne pouvez pas accéder à votre administrateur en raison d’une charge importante, vous pouvez utiliser l’API Fastly pour configurer les règles de blocage :

1. Créez la liste de contrôle d’accès comme décrit dans le document Fastly [&#x200B; Utilisation des listes de contrôle d’accès à l’aide de l’API &#x200B;](https://docs.fastly.com/guides/access-control-lists/working-with-acls-using-the-api) .
1. Dans la section `recv`, créez un fragment de code VCL avec le contenu suivant, après avoir remplacé ACL\_NAME\_GOES\_HERE par le nom de la liste de contrôle d’accès créée à l’étape précédente :

   ```
   if( req.http.Fastly-Client-IP ~ ACL_NAME_GOES_HERE ) {
   error 403 "Forbidden";
   }
   ```

Pour plus d’informations sur le blocage des adresses IP, consultez le guide [Fastly Adobe Commerce Module](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) dans GitHub.
