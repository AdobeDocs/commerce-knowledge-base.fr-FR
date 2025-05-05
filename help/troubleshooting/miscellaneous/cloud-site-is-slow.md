---
title: Le site cloud est lent
description: Cet article fournit des recommandations sur la manière de rendre votre site d’infrastructure cloud Adobe Commerce plus performant sous des charges de trafic élevées et de réduire cette charge.
exl-id: 144df36b-6305-4e57-b813-46bbb0ddedda
feature: Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 0%

---

# Le site cloud est lent

Cet article fournit des recommandations sur la manière de rendre votre site d’infrastructure cloud Adobe Commerce plus performant sous des charges de trafic élevées et de réduire cette charge.

## Versions et éditions affectées

* Adobe Commerce sur l’infrastructure cloud, toutes les versions

## Problème

<u>Étapes à reproduire</u>

1. Visitez votre boutique Adobe Commerce.
1. Parcourez une page de catégorie.
1. Ajoutez un produit au panier.

<u>Résultat attendu</u>

Le site est réactif et l’ajout d’un produit au panier est rapide.

<u>Résultat réel</u>

Le site est lent ou les pages de catégorie sont rapides, mais la page de panier est lente.

## Étapes et solutions de débogage

Procédez comme suit pour déterminer la raison de la lenteur des performances et la corriger. Vous pouvez passer aux premières et deuxième étapes, mais vous ne pouvez bloquer les adresses IP que si l’optimisation des paramètres du cache ne vous aide pas.

1. Vérifiez le taux d’accès au cache des pages à trafic élevé et réduisez la quantité de données lourdement mises à jour.
1. Vérifiez le taux d’accès global au cache du site et la configuration générale du cache/Fastly.
1. Identifiez les clients web à l’origine de la charge de serveur élevée et bloquez les adresses IP à l’origine de la charge élevée.

Les paragraphes suivants fournissent des détails supplémentaires pour chaque étape.

### Étape 1 : vérifiez le taux d’accès au cache pour les pages à trafic élevé.

La première étape pour corriger un site enlisé par un trafic important consiste à s’assurer que les pages comportant le trafic le plus important, comme la page d’accueil du magasin et les pages de catégories de niveau supérieur, sont correctement mises en cache.

Vous pouvez connaître les taux d’accès au cache de ces pages en examinant les en-têtes HTTP `X-Cache` à l’aide de cURL, comme décrit dans la section [Vérification du cache à l’aide de cURL](https://docs.fastly.com/guides/debugging/checking-cache#using-curl) de la documentation Fastly. Vous pouvez également vérifier les mêmes en-têtes à l’aide de l’onglet réseau de la barre d’outils du développeur de votre navigateur web préféré.

Respecte généralement très bien les en-têtes de réponse provenant de l’application. Toutefois, si tous les en-têtes sont définis sur &quot;ne pas mettre en cache&quot; et que la page &quot;arrive à expiration dans le passé&quot;, Fastly ne peut pas mettre en cache la page.

>[!WARNING]
>
>Notez que modifie rapidement les en-têtes de réponse. Par conséquent, la vérification de l’URL principale avec cURL ou le navigateur web n’affichera pas nécessairement les en-têtes émis par l’application. Il est courant que Fastly réponde aux navigateurs web avec des en-têtes &quot;sans cache&quot;, mais que l’application web elle-même autorise la mise en cache et que Fastly mette correctement l’élément en cache. Ainsi, les informations &quot;cache-control&quot; et &quot;pragma&quot; headers ne seront pas utiles dans ce cas.

#### Dépannage des pages à trafic élevé

Si le taux d’accès de la page d’index est faible, vous pouvez le corriger en réduisant la quantité de données lourdement mises à jour présentes sur cette page.

### Étape 2 : Vérifier le taux d’accès global au cache du site

Pour vérifier le taux d’accès global au cache :

1. [ Obtenez des informations d’identification rapides ](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration) pour votre environnement Adobe Commerce sur l’infrastructure cloud.
1. Exécutez la commande cURL Linux/macOS suivante pour vérifier le taux d’accès à votre site au cours des 30 dernières minutes, en le remplaçant par les valeurs de vos informations d’identification Fastly :

   `curl -H "Fastly-Key: " https://api.fastly.com/stats/service//field/hit_ratio?by=minute | json_pp`

   Vous pouvez également vérifier les taux d’accès historiques sur le dernier jour ou mois en modifiant l’option de requête de période de `?by=minute` à `?by=hour` ou `?by=day`. Pour plus d’informations sur l’obtention de statistiques de mise en cache rapides, voir [Options de requête](https://docs.fastly.com/api/stats#Query) dans la documentation Fastly.

   L’option `| json_pp` imprime correctement la sortie de la réponse JSON à l’aide de l’utilitaire `json_pp`. Si vous obtenez l’erreur &#39;_&#39;json\_pp introuvable&#39;_, installez l’utilitaire `json_pp` ou utilisez un autre outil de ligne de commande pour la jolie impression JSON. Vous pouvez également supprimer le paramètre `| json_pp` et exécuter à nouveau la commande . Le résultat de la réponse JSON n’est pas formaté, mais vous pouvez l’exécuter via un embelleur JSON pour le nettoyer.

Un taux d’accès supérieur à 0,90 ou 90 % indique que le cache de la page entière fonctionne.

Un taux d’accès inférieur à 0,85 ou 85 % peut indiquer un problème de configuration du site, ou vous pouvez avoir installé une extension tierce qui n’autorise pas la mise en cache de son contenu.

#### Dépannage du taux d’accès global au cache

1. À l’aide des statistiques de taux d’accès horaire et quotidien, identifiez le moment où le taux d’accès a commencé à diminuer. Si le taux d’accès a soudainement chuté au moment où vous avez déployé une modification sur votre site, envisagez de revenir en arrière jusqu’à ce que le chargement du site diminue.
1. Vérifiez la configuration dans l’administrateur Commerce, sous **Magasins** > **Configuration** > Avancé > **Système** > **Cache de page complet**. Assurez-vous que la valeur **TTL pour le contenu public** n’est pas définie trop bas.
1. Assurez-vous d’avoir [téléchargé les fragments de code VCL](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
1. Si vous utilisez des fragments de code VCL personnalisés, déboguez-les pour une utilisation correcte des actions &quot;pass&quot; ou &quot;tuyau&quot; : ils doivent être utilisés avec précaution et au moins utilisés avec une condition d’un certain type. Pour plus d’informations, voir [Fragments de code VCL personnalisés Fastly](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) dans notre documentation destinée aux développeurs.

### Étape 3 : Identifier les sites web à l’origine de la charge élevée du serveur

Vous pouvez utiliser l’une des méthodes suivantes pour obtenir des informations sur les adresses IP qui accèdent à votre boutique Adobe Commerce.

* Vérifiez les journaux d’accès HTTP par le biais d’une session SSH.
* Contactez l’assistance d’Adobe Commerce pour demander une liste des adresses IP qui entraînent une charge importante sur le site.

#### Vérification des journaux d’accès HTTP

Pour afficher le journal des accès à votre site, exécutez la commande suivante à partir de votre environnement de développement local :

```bash
magento-cloud log access
```

Afficher d’autres lignes avec la fonction

```bash
--lines
```

par exemple :

```bash
magento-cloud log access --lines=500
```

Vous pouvez afficher ce journal et vérifier si une grande partie des demandes provient d’une adresse IP spécifique. Une autre méthode consiste à utiliser `awk` , `sort` et `uniq` pour comptabiliser automatiquement les adresses IP les plus fréquentes dans le journal, comme suit :

```bash
magento-cloud log access --lines 2000 | awk '{print $1}' | sort | uniq -c | sort
  -nr
```

Si la variable

```bash
magento-cloud log
```

ne fonctionne pas, vous pouvez vous connecter au serveur distant avec SSH et vérifier le fichier journal à l’adresse `/var/log/access.log`.

Après avoir identifié les adresses IP à l’origine d’une charge importante du serveur, vous pouvez les bloquer en configurant une liste bloquée IP à partir du panneau d’administration de Commerce, sous **Magasins** > **Configuration** > AVANCÉ > **Système** > **Cache de page complet** > **Configuration rapide** > **Blocking**&rbrace;.

Si vous ne pouvez pas accéder à votre administrateur en raison d’une charge importante, vous pouvez utiliser l’API Fastly pour configurer les règles de blocage :

1. Créez l’ACL comme décrit dans le document [Utilisation des ACL à l’aide de l’API](https://docs.fastly.com/guides/access-control-lists/working-with-acls-using-the-api) Fastly.
1. Dans la section `recv` , créez un extrait de code VCL avec le contenu suivant, en remplaçant ACL\_NAME\_GOES\_HERE par le nom de l’ACL qui a été créé à l’étape précédente :

   ```
   if( req.http.Fastly-Client-IP ~ ACL_NAME_GOES_HERE ) {
   error 403 "Forbidden";
   }
   ```

Pour plus d’informations sur le blocage des adresses IP, consultez le [guide du module Fastly Adobe Commerce](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) dans GitHub.
