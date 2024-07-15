---
title: Goulot d’étranglement de charge élevée MySQL dans Adobe Commerce sur l’infrastructure cloud
description: Cette rubrique aborde une solution lorsque la charge élevée de MySQL entraîne un problème de goulot d’étranglement des performances dans Adobe Commerce sur l’infrastructure cloud.
exl-id: c1f9d282-41d8-4850-8a24-336d55aa3140
feature: Cloud, Observability, Paas, Services
role: Developer
source-git-commit: 075f55b94202f75839abd25bd47824eeb5226485
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Goulot d’étranglement de charge élevée MySQL dans Adobe Commerce sur l’infrastructure cloud

Cette rubrique aborde une solution lorsque la charge élevée de MySQL entraîne un problème de goulot d’étranglement des performances dans Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur les comptes d’infrastructure cloud 2.x.x, Pro.

### Conditions préalables

* Outils de la CEE version 2002.0.16 et ultérieure
* Service New Relic APM (**Votre compte Adobe Commerce sur l’infrastructure cloud inclut le logiciel du service New Relic APM** avec une clé de licence.)

Pour plus d’informations sur le service New Relic APM et sa configuration avec votre compte Adobe Commerce sur l’infrastructure cloud, accédez à [Services New Relic](https://devdocs.magento.com/guides/v2.3/cloud/project/new-relic.html) et [Introduction à l’APM New Relic](https://docs.newrelic.com/docs/apm/new-relic-apm/getting-started/introduction-apm/).

## Problème

<u> Étapes Pour Savoir Si Le Problème Vous Affecte </u>

1. Dans votre graphique d’aperçu APM New Relic, recherchez la première indication que MySQL est devenu un goulot d’étranglement. Consultez l’exemple ci-dessous, où MySQL est devenu un goulot d’étranglement et prend la plupart du temps pour les transactions web :

   ![KB-372_image002.png](assets/KB-372_image002.png)

   Remarquez que la ligne en pointillés rouges dans l’image affiche une tendance à la hausse perceptible dans le temps des transactions Web MySQL, puis atteint des niveaux encore plus élevés.
1. À partir de là, vous pouvez accéder à l’écran **Base de données** où vous pouvez voir la deuxième indication de débit élevé ou de requêtes `SELECT` lentes dans MySQL. Dans l’exemple ci-dessous, vous pouvez voir lors du tri par **Le plus long temps consommé**, votre boutique, dans cet exemple, est lente sur les requêtes MySQL `SELECT`.

   ![KB-372_image003_BlurredExtension.png](assets/KB-372_image003_BlurredExtension.png)

Analysez les transactions lentes dans New Relic APM. Si vous constatez un volume élevé de requêtes ou une pression élevée sur une base de données MySQL, vous pouvez répartir la charge sur différents noeuds en activant les connexions `SLAVE`.

## Cause

Votre boutique Adobe Commerce sur l’infrastructure cloud a un débit élevé ou est lente sur les requêtes MySQL `SELECT`.

## Solution

>[!WARNING]
>
>Pour l’architecture mise à l’échelle (architecture partagée), les connexions esclaves Redis **NE DOIVENT PAS** être activées. Vous pouvez vérifier si vous utilisez une architecture mise à l’échelle en accédant à l’URL de votre projet, par exemple `https://console.adobecommerce.com/<owner-user-name>/<project-ID>/<environment-name>`. Cliquez sur **[!UICONTROL SSH]**. S’il y a plus de trois noeuds, vous utilisez une architecture mise à l’échelle. Si vous activez Redis Slave Reads sur une architecture mise à l’échelle, le client recevra des erreurs sur les connexions Redis ne pouvant pas se connecter. Cela concerne la manière dont les grappes sont configurées pour traiter les connexions Redis. Redis Les esclaves sont toujours actifs, mais ne seront pas utilisés pour Redis Reads. Nous recommandons que l’architecture mise à l’échelle utilise Adobe Commerce 2.3.5 ou version ultérieure, et mette en oeuvre la nouvelle configuration du serveur principal Redis et mette en oeuvre la mise en cache L2 pour Redis.

Si vous rencontrez ces deux indications, l’activation de `SLAVE` connexions pour la base de données MySQL et Redis peut aider à répartir la charge sur différents noeuds.

Adobe Commerce peut lire plusieurs bases de données ou Redis de manière asynchrone. Mettre à jour le fichier `.magento.env.yaml` en définissant sur `true` les valeurs `MYSQL_USE_SLAVE_CONNECTION` et `REDIS_USE_SLAVE_CONNECTION` pour utiliser une connexion **lecture seule** à la base de données pour recevoir le trafic en lecture seule sur un noeud non maître. Cela améliore les performances grâce à l’équilibrage de charge, car un seul noeud doit gérer le trafic lecture-écriture. Définissez cette variable sur `false` pour supprimer tout tableau de connexion en lecture seule existant du fichier `env.php`.

### Étapes

1. Modifiez votre fichier `.magento.env.yaml` et ajoutez le contenu suivant :

   ![KB-372_image004.png](assets/KB-372_image004.png)

   Pour plus d’informations, reportez-vous à la section [Déploiement de variables dans DevDocs](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection).

1. Validez vos modifications et poussez-les.
1. La publication des modifications lancera un nouveau processus de déploiement. Une fois le déploiement terminé, votre instance Adobe Commerce sur l’infrastructure cloud doit maintenant être configurée pour utiliser les connexions esclaves.

## Questions courantes

Vous trouverez ci-dessous les questions courantes que vous pouvez vous poser lorsque vous envisagez d’utiliser la fonctionnalité Connexions esclaves pour votre Adobe Commerce sur la boutique d’infrastructures cloud.

* Existe-t-il des problèmes ou des limitations connus pour utiliser les connexions esclaves ? **Nous ne connaissons aucun problème lors de l’utilisation des connexions esclaves. Assurez-vous simplement d’utiliser le module d’outils de la pièce le plus récemment mis à jour. Les instructions se trouvent ici sur [la mise à jour de votre package ece-tools](https://devdocs.magento.com/cloud/project/ece-tools-update.html).**
* Existe-t-il une latence supplémentaire en utilisant les connexions esclaves ? *Oui, la latence entre AZ (zones de disponibilité croisée) est plus élevée et réduit les performances d’une instance Adobe Commerce sur l’infrastructure cloud dans le cas où l’instance n’est pas surchargée et peut transporter la charge entière. Mais clairement, si l&#39;instance est surchargée - master-slave va vous aider à obtenir des performances en répartissant la charge sur la base de données MySQL ou les redis sur différents noeuds.*

  **Sur les grappes non surchargées** - **Les connexions esclaves vont ralentir les performances de 10 à 15 %**, ce qui est l’une des raisons pour lesquelles elles ne sont pas par défaut.

  *Mais sur les grappes surchargées, il y a une amélioration des performances car ces 10 à 15 % sont atténués en réduisant la charge par le trafic.*
* Dois-je activer ces paramètres pour ma boutique ? *Si vous avez une charge élevée ou si vous attendez une charge élevée sur la base de données MySQL ou sur Redis, vous devez absolument activer les connexions esclaves. Pour un client ordinaire avec un trafic moyen, il s&#39;agit **pas**d&#39;un paramètre optimal à activer.*

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [Déployer des variables](https://devdocs.magento.com/cloud/env/variables-deploy.html).
* [Configurez la réplication de base de données facultative](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master_slavedb.html).
* [Module ece-tools](https://devdocs.magento.com/cloud/reference/ece-tools-reference.html).

>[!NOTE]
>
>Nous sommes conscients que cet article peut encore contenir des termes logiciels standards de l&#39;industrie que certains peuvent trouver racistes, sexistes ou oppressifs, et qui peuvent faire que le lecteur se sent blessé, traumatisé, ou mal accueilli. Adobe s’efforce de supprimer ces termes de notre code, de notre documentation et de nos expériences utilisateur.
