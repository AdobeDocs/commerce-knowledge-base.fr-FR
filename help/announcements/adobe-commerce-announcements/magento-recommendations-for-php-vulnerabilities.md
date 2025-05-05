---
title: Vulnérabilités d’Adobe Commerce Recommendations pour PHP
description: Le 3 septembre, le Centre de partage et d'analyse d'informations à plusieurs états (MS-ISAC) a publié une alerte relative à plusieurs vulnérabilités qui pourraient permettre l'exécution arbitraire de code et une recommandation que tous les sites utilisant PHP doivent mettre à jour au plus tard la version PHP ASAP ([l'alerte complète est disponible ici](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).
exl-id: 0bc7caab-0b89-463a-a7f2-a7c92df9f84e
feature: Compliance, Recommendations
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Vulnérabilités d’Adobe Commerce Recommendations pour PHP

Le 3 septembre, le Centre de partage et d&#39;analyse d&#39;informations à plusieurs états (MS-ISAC) a publié une alerte relative à plusieurs vulnérabilités qui pourraient permettre l&#39;exécution arbitraire de code et une recommandation que tous les sites utilisant PHP doivent mettre à jour vers la dernière version de PHP ASAP ([l&#39;alerte complète est disponible ici](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).

>[!WARNING]
>
>Sur Adobe Commerce sur l’infrastructure cloud, notez que les mises à niveau de service ne peuvent pas être transférées vers l’environnement de production sans préavis de 48 heures ouvrables à notre équipe d’infrastructure. Cela est nécessaire, car nous devons nous assurer qu’un ingénieur du support de l’infrastructure est disponible pour mettre à jour votre configuration dans les délais voulus, avec un temps d’arrêt minimal pour votre environnement de production. Ainsi, 48 heures avant le moment où vos modifications doivent être en production [envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) détaillant la mise à niveau de service requise et indiquant l’heure à laquelle vous souhaitez que le processus de mise à niveau démarre.

Lisez la suite pour connaître les impacts et les étapes des sites Adobe Commerce :

**Adobe Commerce hébergée sur notre produit cloud**

Si vous utilisez Adobe Commerce sur l’infrastructure cloud, veuillez travailler avec votre équipe technologique pour redéployer Adobe Commerce à tout moment\* afin de tirer parti de la mise à jour. Nous recommandons aux commerçants d’effectuer ce redéploiement d’ici le 30 septembre afin d’éviter les problèmes de conformité PCI qui peuvent entrer en vigueur en raison de ces vulnérabilités à la fin du mois.

Remarques supplémentaires sur le redéploiement de votre site Cloud pour cette mise à jour :

* Si votre site utilise toujours la version 7.0 de PHP, vous devrez d’abord effectuer une mise à niveau vers une version de PHP prise en charge avant de procéder au redéploiement afin de tirer parti de ces mises à jour de sécurité.
* Pour 2.1.x/2.2.x, plus d&#39;informations sur la mise à niveau de PHP sont disponibles [ici](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=fr).

\* *Les versions précédentes de cet article et notre messagerie ont commencé le 19 septembre, mais nos équipes ont terminé leur travail avant l&#39;emploi du temps.*

**Adobe Commerce sur toutes les autres solutions d&#39;hébergement**

Comme Adobe Commerce repose sur PHP, nous recommandons à tous les commerçants utilisant Adobe Commerce de passer en revue les mises à jour nécessaires pour le PHP avec leur fournisseur d’hébergement. Nous recommandons également aux commerçants de terminer cette révision et toute mise à jour d’ici le 30 septembre afin d’éviter les problèmes de conformité PCI qui peuvent entrer en vigueur en raison de ces vulnérabilités à la fin du mois.

Notez quelques détails supplémentaires pour Adobe Commerce sur les autres solutions d’hébergement :

* Les versions 2.0 ou 1.x d&#39;Adobe Commerce qui utilisent des versions PHP antérieures à la version 7.1 ou ultérieure n&#39;ont pas de correctif PHP officiel disponible. Le chemin recommandé est de mettre à niveau PHP vers une version PHP prise en charge.

Selon l&#39;alerte, les correctifs recommandés pour cette vulnérabilité incluent :

* PHP 7.1 : [https://www.php.net/ChangeLog-7.php\#7.1.32](https://www.php.net/ChangeLog-7.php#7.1.32)
* PHP 7.2 : [https://www.php.net/ChangeLog-7.php\#7.2.22](https://www.php.net/ChangeLog-7.php#7.2.22)
* PHP 7.3 : [https://www.php.net/ChangeLog-7.php\#7.3.9](https://www.php.net/ChangeLog-7.php#7.3.9)

Si vous souhaitez plus d&#39;informations sur PHP et les versions récentes, vous pouvez visiter le [site de PHP](https://www.php.net/). Si vous avez des questions ou souhaitez plus d’informations sur les bonnes pratiques en matière de sécurité, consultez notre [Guide des bonnes pratiques de sécurité](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf).
