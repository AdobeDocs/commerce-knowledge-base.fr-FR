---
title: FAQ sur la politique de cycle de vie mise à jour pour les versions d’Adobe Commerce
description: "Adobe Commerce fournit des correctifs de qualité pour une version mineure pendant un minimum de 12 mois à compter de la date de disponibilité générale de la prochaine version mineure du logiciel. La manière dont nous fournissons des correctifs de qualité au cours de cette période est en train de changer :"
exl-id: 4aa601d0-ee1d-4f1f-a684-188772a58dd1
feature: Compliance, Support
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 0%

---

# FAQ sur la politique de cycle de vie mise à jour pour les versions d’Adobe Commerce

## Qu&#39;est-ce qui change ?

Adobe Commerce fournit des correctifs de qualité pour une version mineure pendant un minimum de 12 mois à compter de la date de disponibilité générale de la prochaine version mineure du logiciel. La manière dont nous fournissons des correctifs de qualité au cours de cette période est en train de changer :

* **Stratégie précédente :** Actuellement, les correctifs de qualité de la ligne précédente qui se trouve dans la fenêtre EOS de 12 mois sont livrés via notre version trimestrielle de correctifs, ce qui fait des correctifs trimestriels une combinaison de sécurité + qualité.
* **Nouvelle stratégie :** À compter de la version 2.4 comme ligne de mise à jour mineure la plus récente, les correctifs de mise à jour de la ligne prise en charge précédente (2.3) seront uniquement mis en sécurité. Nous fournissons toujours des correctifs de qualité pour la ligne prise en charge précédente pendant la période de 12 mois après la publication d’une version mineure (telle la version 2.4) et des nouvelles lignes de mise à jour mineures suivantes ; mais ils seront disponibles via [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) et ne se concentrer que sur les questions critiques.

## Quand cette politique entre-t-elle en vigueur ?

La sortie d’Adobe Commerce 2.3.6 est prévue pour le 15 octobre 2020. Il s’agit de la dernière version de correctif pour Adobe Commerce 2.3 qui inclura à la fois la qualité et la sécurité. Après la version 2.3.6, la ligne 2.3.x deviendra uniquement sécurisée et les problèmes de qualité critiques de la version 2.3 peuvent être résolus via QPT.

>[!NOTE]
>
>La seule fois où nous publierons une version complète de la version 2.3 est si nous devons maintenir la conformité avec notre pile technologique, comme pour PHP ou Elasticsearch. Cela se passe au 2e trimestre 2021 avec une mise à jour obligatoire de PHP 7.4, nous allons augmenter la ligne à 2.3.7. Pour plus d’informations, voir [Prise en charge de PHP 7.4 pour la ligne de version Adobe Commerce 2.3.x](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) Publication DevBlog .

## Qu’est-ce qu’une version sécurisée uniquement ?

Les versions de sécurité uniquement contiennent des correctifs de sécurité uniquement et aucune qualité n’est corrigée. Notez toutefois que nos versions de sécurité uniquement peuvent inclure des correctifs spécifiques lorsque nous les jugeons absolument essentiels pour exécuter Adobe Commerce.

## Y aura-t-il toujours une version de sécurité uniquement pour la dernière ligne (à compter de la publication, 2.4) ?

Adobe continuera également à disposer de versions de sécurité uniquement pour la dernière ligne de mise à jour. Le processus à suivre est présenté dans la section [Présentation de la nouvelle version du correctif uniquement pour la sécurité](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287) Publication DevBlog .

## Qu’est-ce que l’outil Correctifs de qualité ?

Reportez-vous à [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) article de notre base de connaissances en matière de soutien.

## Qui devrait envisager d’utiliser cette nouvelle politique ?

La nouvelle politique vise à créer des voies permettant aux commerçants de planifier stratégiquement les coûts annuels de développement d&#39;Adobe Commerce, tout en leur permettant de maintenir la sécurité et la qualité critique pendant ces cycles stratégiques. Il peut également être utilisé par les commerçants qui se soucient de la sécurité sur tout le reste et qui sont généralement satisfaits de la stabilité d’une ligne plus ancienne et prise en charge. Les commerçants peuvent trouver plus facile de planifier et de financer ces mises à niveau, car elles seront plus prévisibles.

## Les commerçants doivent-ils toujours passer à la dernière ligne ?

En fin de compte, tous les commerçants doivent encore donner la priorité à la planification de l’adoption de la dernière ligne Adobe Commerce en temps voulu. La nouvelle ligne Sécurité uniquement et l’outil QPT ne sont pas destinés à remplacer la feuille de route de la mise à niveau stratégique pour les commerçants ; ils offrent plutôt une certaine flexibilité aux marchands qui planifient leur feuille de route de mise à niveau et un moyen de réagir rapidement aux problèmes de sécurité/qualité sans avoir à mettre en oeuvre une mise à niveau complète.

## Comment obtenir des correctifs de qualité sur les versions mineures prises en charge qui ne sont pas la dernière ligne ?

Les correctifs seront mis à disposition via le [Outil Correctifs de qualité](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).

## Comment obtenir des correctifs de qualité sur la dernière ligne ?

La ligne actuelle sera de qualité dans le cadre de la mise à jour trimestrielle. Entre les versions, si vous contactez le support pour un correctif sur la ligne la plus récente, il le fournira via QPT. Ensuite, une fois que vous avez effectué la mise à niveau vers la version contenant ce correctif, celui-ci sera appliqué via le correctif trimestriel.

## Quels types de problèmes de qualité seront corrigés sur les versions mineures prises en charge qui ne sont pas la dernière ligne ?

Seuls les problèmes de qualité majeurs qui rompent les flux principaux seront corrigés à la ligne précédente (2.3) et diffusés via QPT.

## Des correctifs de qualité feront-ils partie de la version trimestrielle sur les versions mineures prises en charge qui ne sont pas la dernière ligne en date ?

Oui, dans le cadre de la ligne sécurité uniquement, nous publions ce que l’Adobe appelle des &quot;correctifs&quot; sur cette ligne. Il s’agit de problèmes très critiques qui affectent l’application Adobe Commerce.

## Les améliorations de sécurité et le QPT seront-ils fournis en même temps ?

La ligne de sécurité uniquement suivra le calendrier trimestriel de publication et sera publiée avec la nomenclature -p1. Exemple 2.3.6-p1. La qualité sera publiée ad hoc lorsque des problèmes de qualité seront découverts et corrigés, et ils seront rendus disponibles via QPT.

## Si un problème de qualité ne sera pas résolu dans les versions mineures prises en charge qui ne sont pas la dernière ligne ou QPT, que dois-je faire ?

La ligne précédente étant uniquement sécurisée, l’avantage principal reste sécurisé. Seuls les correctifs pour les problèmes majeurs qui rompent les flux principaux seront disponibles via QPT.

Les problèmes qui n’affectent pas les flux principaux ou qui comportent des solutions seront corrigés dans la ligne la plus récente uniquement. Adobe encourage ceux qui souhaitent des correctifs critiques et non critiques à passer à la ligne la plus récente.

## Les mises à niveau seront-elles plus coûteuses ou plus difficiles pour les commerçants s’ils restent sur la ligne de sécurité uniquement jusqu’à ce qu’elle atteigne la fin de la prise en charge de la sécurité ?

En théorie, ils devraient être égaux en coûts pour le commerçant en termes d&#39;heures de développement tant qu&#39;ils n&#39;ont pas adopté un grand nombre de correctifs de qualité. Si un commerçant trouve qu’il a besoin ou souhaite plus d’une poignée de correctifs via l’outil QPT, la recommandation consiste à privilégier une mise à niveau vers la dernière version d’Adobe Commerce. L’adoption d’un grand nombre de correctifs de qualité, au lieu d’effectuer une mise à niveau vers la version actuelle d’Adobe Commerce, peut augmenter les coûts de développement et les complexités de la mise à niveau une fois que la ligne de sécurité uniquement atteint la fin de la prise en charge.

## Pourquoi limiter la quantité de correctifs de qualité délivrés via QPT ?

En appliquant de nombreux correctifs de qualité individuels, vous rendez votre code Adobe Commerce plus complexe. Cette complexité supplémentaire peut entraîner des modifications imprévisibles lors de la mise à niveau vers la ligne de mise à jour la plus récente. C’est pourquoi nous vous recommandons d’utiliser le protocole QPT avec parcimonie et uniquement pour les correctifs les plus critiques.

## Qu’en est-il de la conformité pour les piles de technologies ?

Au cours de la durée de vie d’une ligne de mise à jour, diverses piles de technologies telles que PHP ou Elasticsearch devront être mises à niveau pour rester conformes. Nous donnerons autant de préavis que possible à nos commerçants que ceux-ci arrivent.

Remarque : Au 2e trimestre 2021, nous devrons mettre à jour PHP et Redis sur la ligne 2.3.x pour rester en conformité. La ligne est alors incrémentée à 2.3.7. Pour plus d’informations, voir [Prise en charge de PHP 7.4 pour la ligne de version Adobe Commerce 2.3.x](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) Publication DevBlog .
