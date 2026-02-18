---
title: Recommandations Adobe Commerce pour les vulnérabilités PHP
description: Le 3 septembre, le Multi-State Information Sharing and Analysis Center (MS-ISAC) a publié une alerte concernant plusieurs vulnérabilités qui pourraient permettre l'exécution de code arbitraire et une recommandation que tous les sites utilisant PHP devraient mettre à jour vers la dernière version de PHP dès que possible ([l'alerte complète est disponible ici](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).
exl-id: 0bc7caab-0b89-463a-a7f2-a7c92df9f84e
feature: Compliance, Recommendations
role: Admin
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Recommandations Adobe Commerce pour les vulnérabilités PHP

Le 3 septembre, le Multi-State Information Sharing and Analysis Center (MS-ISAC) a émis une alerte concernant plusieurs vulnérabilités qui pourraient permettre l&#39;exécution de code arbitraire et une recommandation que tous les sites utilisant PHP devraient mettre à jour vers la dernière version de PHP dès que possible ([alerte complète est disponible ici](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).

>[!WARNING]
>
>Concernant Adobe Commerce sur les infrastructures cloud, veuillez noter que les mises à niveau de service ne peuvent pas être envoyées à l’environnement de production sans préavis de 48 heures ouvrables à notre équipe en charge de l’infrastructure. Cela est nécessaire car nous devons nous assurer qu’un ingénieur du support à l’infrastructure est disponible pour mettre à jour votre configuration dans le délai souhaité avec un temps d’arrêt minimal pour votre environnement de production. Ainsi, 48 heures avant le moment où vos modifications doivent être mises en production [soumettez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) détaillant la mise à niveau de service requise et indiquant l’heure à laquelle vous souhaitez que le processus de mise à niveau démarre.

Lisez la suite pour connaître les impacts et les étapes pour les sites Adobe Commerce :

**Adobe Commerce hébergé sur notre produit Cloud**

Si vous utilisez Adobe Commerce sur une infrastructure cloud, travaillez avec votre équipe technologique pour redéployer Adobe Commerce à tout moment afin de tirer parti de la mise à jour. Nous recommandons aux commerçants de terminer ce redéploiement d&#39;ici le 30 septembre afin d&#39;éviter les problèmes de conformité PCI qui pourraient entrer en vigueur à la suite de ces vulnérabilités à la fin du mois.

Notes supplémentaires sur le redéploiement de votre site cloud pour cette mise à jour :

* Si votre site utilise toujours PHP version 7.0, vous devrez d&#39;abord effectuer une mise à niveau vers une version PHP prise en charge avant de redéployer afin de profiter de ces mises à jour de sécurité.
* Pour 2.1.x/2.2.x, plus d&#39;informations sur la mise à niveau de PHP peuvent être trouvées [ici](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html).

\* *Les versions précédentes de cet article et de notre message indiquaient le 19 septembre, mais nos équipes ont terminé leur travail plus tôt que prévu.*

**Adobe Commerce sur toutes les autres solutions d’hébergement**

Comme Adobe Commerce s&#39;appuie sur PHP, nous recommandons à tous les commerçants qui utilisent Adobe Commerce de passer en revue les mises à jour nécessaires pour PHP avec leur fournisseur d&#39;hébergement. Nous recommandons également aux commerçants de terminer cet examen et toute mise à jour d&#39;ici le 30 septembre afin d&#39;éviter les problèmes de conformité PCI qui pourraient entrer en vigueur à la suite de ces vulnérabilités à la fin du mois.

Veuillez noter quelques détails supplémentaires pour Adobe Commerce sur d’autres solutions d’hébergement :

* Les versions 2.0 ou 1.x d’Adobe Commerce qui utilisent des versions PHP antérieures à la version 7.1 ou supérieure ne disposent pas de patch PHP officiel. Le chemin recommandé est de mettre à niveau PHP vers une version supportée.

Selon l’alerte, les correctifs recommandés pour cette vulnérabilité incluent :

* PHP 7.1 : [https://www.php.net/ChangeLog-7.php\#7.1.32](https://www.php.net/ChangeLog-7.php#7.1.32)
* PHP 7.2 : [https://www.php.net/ChangeLog-7.php\#7.2.22](https://www.php.net/ChangeLog-7.php#7.2.22)
* PHP 7.3 : [https://www.php.net/ChangeLog-7.php\#7.3.9](https://www.php.net/ChangeLog-7.php#7.3.9)

Si vous souhaitez plus d&#39;informations sur PHP et les versions récentes, vous pouvez visiter le site de [PHP](https://www.php.net/). Si vous avez des questions ou souhaitez obtenir plus d’informations sur les bonnes pratiques en matière de sécurité, consultez notre [&#x200B; Guide des bonnes pratiques de sécurité &#x200B;](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf).
