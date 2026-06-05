---
title: Recherche d’une attaque DDoS à partir de l’interface de ligne de commande
description: Cet article aborde le problème de la vérification des attaques par déni de service distribué (DDoS) à partir de l’interface de ligne de commande (CLI) de votre serveur.
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 0%

---

# Recherche d’une attaque DDoS à partir de l’interface de ligne de commande

Cet article aborde le problème de la vérification des attaques par déni de service distribué (DDoS) à partir de l’interface de ligne de commande (CLI) de votre serveur.

## Produits et versions concernés

* Adobe Commerce, toutes versions
* Magento Open Source, toutes versions

## Problème

Votre site Web est lent et vous n&#39;avez pas accès à d&#39;autres outils d&#39;application d&#39;analyse, autres que votre interface de ligne de commande, pour vérifier la présence d&#39;une attaque DDoS potentielle. Les symptômes d&#39;une attaque DDoS peuvent varier considérablement en fonction de votre configuration réseau, des logiciels utilisés, etc.

Cependant, il est recommandé d’utiliser des produits logiciels d’analyse spécialement conçus pour vous aider à identifier les attaques DDoS.

## Cause

Il existe plusieurs causes possibles à la lenteur d’un site web, notamment un serveur aux performances lentes, une utilisation élevée de CPU ou une configuration incorrecte des scripts, du code ou du matériel bon marché. Parfois, cela peut être dû à une attaque DDoS. Deux des outils de base dont vous disposez pour détecter une attaque DDoS sont vos journaux Adobe Commerce et votre interface de ligne de commande.

Encore une fois, il est important de noter que l&#39;utilisation de logiciels spécialement conçus pour identifier les attaques DDoS serait très utile dans votre enquête.

## Étapes de la solution

1. Vérifiez vos journaux Adobe Commerce pour voir si autre chose qu’une attaque DDoS se produit. Pour plus d’informations, reportez-vous aux articles suivants de notre documentation destinée aux développeurs :
   * [Emplacements des journaux Adobe Commerce et Magento Open Source](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/enable-logging)
   * [Emplacements des journaux d’Adobe Commerce sur le cloud infrastructure](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/test/log-locations)
1. Commencez à utiliser l’interface de ligne de commande pour vérifier toutes vos connexions Internet actuelles à l’aide de la commande `netstat` : `netstat -na`. Toutes les connexions actives établies au serveur s’affichent. Vous remarquerez peut-être qu’il y a trop de connexions provenant de la même adresse IP.
1. Pour limiter davantage les résultats de vos connexions établies à ceux qui se connectent uniquement sur le port 80 (le port http de votre site web), afin que vous puissiez trier et reconnaître un trop grand nombre de connexions à partir d’une adresse IP ou d’un groupe d’adresses IP, utilisez la commande suivante : `netstat -an | grep :80 | sort`. Vous pouvez répéter la même commande pour https sur le port 443 : `netstat -an | grep :443 | sort`. Une autre option consiste à étendre la commande d&#39;origine aux deux ports 80 et 443: `netstat -an | egrep ":80|:443" | sort`.
1. Pour voir si plusieurs `SYNC_REC` actives se produisent sur le serveur, utilisez la commande : `netstat -n -p|grep SYN_REC | wc -l` Ce nombre est généralement inférieur à 5, mais il peut être beaucoup plus élevé pour une attaque DDoS, bien que pour certains serveurs, un nombre plus élevé puisse être une condition normale.
1. Pour répertorier toutes les adresses IP qui envoient `SYNC_REC` statuts, utilisez la commande : `netstat -n -p | grep SYN_REC | sort -u`.
1. Pour répertorier toutes les adresses IP uniques qui envoient des statuts de `SYNC_REC`, utilisez la commande : `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’`.
1. Vous pouvez également utiliser la commande `netstat` pour compter et calculer le nombre de connexions que chaque adresse IP établit avec votre serveur : `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Pour répertorier le nombre de connexions de protocole UDP ou TCP connectées à votre serveur, utilisez la commande : `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Pour vérifier les connexions établies, au lieu de toutes les connexions, et afficher le nombre de connexions pour chaque adresse IP, utilisez la commande : `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr`.
1. Pour afficher les nombres de connexions répertoriés par adresse IP au port 80, utilisez la commande : `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`.

Assurez-vous d&#39;avoir quelqu&#39;un pour analyser correctement les données que vous trouvez pour déterminer si vous avez en fait une attaque DDoS. L&#39;utilisation des commandes `netstat` de l&#39;interface de ligne de commande de votre serveur dans les étapes ci-dessus vous aidera à analyser si vous subissez une attaque DDoS, mais l&#39;utilisation de produits d&#39;analyse logicielle spécialement conçus pour vous aider à identifier les attaques DDoS, ainsi que l&#39;analyse appropriée, sont vos meilleurs outils pour identifier les menaces DDoS.

Si vous constatez que vous faites l&#39;objet d&#39;une attaque DDoS, les mesures que vous pouvez prendre dépendent de votre configuration réseau et de la façon dont l&#39;attaque DDoS se produit, mais le conseil général est de contacter votre FAI, d&#39;obtenir une nouvelle adresse IP pour votre serveur, et / ou de consulter des professionnels de l&#39;informatique qualifiés dans le traitement des problèmes DDoS pour analyser et conseiller sur votre situation particulière.

## Informations connexes dans notre documentation destinée aux développeurs :

* [Protection DDoS](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/fastly#ddos-protection)
* [Utilisation des commandes de l’interface de ligne de commande](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli)
* [Cloud CLI pour Commerce](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview)
