---
title: Recherche d’une attaque DDoS à partir de l’interface de ligne de commande
description: Cet article explique comment vérifier les attaques par déni de service (DDoS) provenant de l’interface de ligne de commande de votre serveur.
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# Recherche d’une attaque DDoS à partir de l’interface de ligne de commande

Cet article explique comment vérifier les attaques par déni de service (DDoS) provenant de l’interface de ligne de commande de votre serveur.

## Produits et versions concernés

* Adobe Commerce, toutes versions
* Magento Open Source, toutes versions

## Problème

Votre site web est lent et vous n’avez pas accès à d’autres outils d’application d’analyse, autres que votre interface de ligne de commande, pour rechercher une attaque DDoS potentielle. Les symptômes d’une attaque DDoS peuvent varier considérablement en fonction de la configuration de votre réseau, des logiciels utilisés, etc.

Il est toutefois recommandé d’utiliser des logiciels d’analyse spécialement conçus pour identifier les attaques DDoS.

## Cause

Il existe plusieurs causes possibles à la lenteur d’un site web, notamment un serveur peu performant, une utilisation élevée de l’unité centrale ou une mauvaise configuration dans les scripts, le code ou du matériel bon marché. Parfois, cela peut être dû à une attaque DDoS. Deux des outils de base que vous devez vérifier pour une attaque DDoS sont vos journaux Adobe Commerce et votre interface de ligne de commande.

Encore une fois, il est important de noter que l’utilisation de logiciels spécialement conçus pour identifier les attaques DDoS serait très utile dans votre enquête.

## Étapes de la solution

1. Vérifiez vos journaux Adobe Commerce pour voir si autre chose que l’attaque DDoS se produit. Pour plus d’informations, reportez-vous aux articles suivants de notre documentation destinée aux développeurs :
   * [Emplacements des journaux Adobe Commerce et Magento Open Source](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html)
   * [Adobe Commerce sur les emplacements des journaux d’infrastructure cloud](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html)
1. Commencez à utiliser votre interface de ligne de commande pour vérifier toutes vos connexions Internet actuelles à l’aide de la commande `netstat` : `netstat -na`. Cette option affiche toutes les connexions établies actives au serveur. Ici, vous pouvez peut-être remarquer trop de connexions provenant de la même adresse IP.
1. Pour affiner davantage vos résultats de connexion établis à ceux qui se connectent sur le port 80 (le port http de votre site web), afin que vous puissiez trier et reconnaître trop de connexions à partir d’une adresse IP ou d’un groupe d’adresses IP, utilisez la commande suivante : `netstat -an | grep :80 | sort`. Vous pouvez répéter la même commande pour https sur le port 443: `netstat -an | grep :443 | sort`. Une autre option consiste à étendre la commande d&#39;origine aux ports 80 et 443 : `netstat -an | egrep ":80|:443" | sort`.
1. Pour voir si plusieurs `SYNC_REC` actifs se produisent sur le serveur, utilisez la commande :     `netstat -n -p|grep SYN_REC | wc -l`     Cette valeur est généralement inférieure à 5, mais elle peut être beaucoup plus élevée lors d’une attaque DDoS, même si, pour certains serveurs, un nombre plus élevé peut être une condition normale.
1. Pour répertorier toutes les adresses IP qui envoient `SYNC_REC` états, utilisez la commande : `netstat -n -p | grep SYN_REC | sort -u`.
1. Pour lister plus en détail toutes les adresses IP uniques qui envoient `SYNC_REC` états, utilisez la commande : `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’`.
1. Vous pouvez également utiliser la commande `netstat` pour compter et calculer le nombre de connexions que chaque adresse IP établit à votre serveur : `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Pour répertorier le nombre de connexions au protocole UDP ou TCP connectées à votre serveur, utilisez la commande : `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Pour vérifier les connexions établies, au lieu de toutes les connexions, et afficher le nombre de connexions pour chaque adresse IP, utilisez la commande : `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr`.
1. Pour afficher le nombre de connexions répertoriées par adresse IP au port 80, utilisez la commande : `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`.

Assurez-vous que vous disposez d’une personne pour analyser correctement les données que vous trouvez afin de déterminer si vous avez effectivement une attaque DDoS. L’utilisation des commandes `netstat` de l’interface de ligne de commande de votre serveur dans les étapes ci-dessus vous aidera à analyser si vous rencontrez une attaque DDoS, mais l’utilisation de produits d’analyse logicielle spécialement conçus pour aider à identifier les attaques DDoS, ainsi qu’une analyse appropriée, constitue votre meilleur outil pour identifier les menaces DDoS.

Si vous constatez que vous êtes attaqué par DDoS, les étapes que vous pouvez suivre dépendent de la configuration de votre réseau et de la façon dont l’attaque par DDoS se produit, mais un conseil général est de contacter votre FAI, d’obtenir une nouvelle adresse IP pour votre serveur et/ou de consulter des professionnels de l’informatique compétents en gestion des problèmes de DDoS pour analyser et conseiller votre situation particulière.

## Lectures connexes dans notre documentation destinée aux développeurs :

* [Protection DDoS](https://devdocs.magento.com/guides/v2.3/cloud/cdn/cloud-fastly.html#ddos-protection)
* [Utilisation de commandes de l’interface de ligne de commande](https://devdocs.magento.com/guides/v2.3/config-guide/deployment/pipeline/example/cli.html)
* [Interface de ligne de commande cloud pour Commerce](https://devdocs.magento.com/guides/v2.3/cloud/reference/cli-ref-topic.html)
