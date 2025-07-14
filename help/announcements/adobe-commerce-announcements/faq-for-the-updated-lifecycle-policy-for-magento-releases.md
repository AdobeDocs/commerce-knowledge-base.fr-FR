---
title: FAQ sur la politique de cycle de vie mise à jour pour les versions d’Adobe Commerce
description: 'Adobe Commerce fournit des correctifs de qualité pour une version mineure pendant au moins 12 mois à compter de la date de disponibilité générale de la prochaine version mineure du logiciel. La manière dont nous fournissons des correctifs de qualité au cours de cette période change :'
exl-id: 4aa601d0-ee1d-4f1f-a684-188772a58dd1
feature: Compliance, Support
role: Admin
source-git-commit: f11596ea844fead42141c7e1fea586b2a11f757a
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---

# FAQ sur la politique de cycle de vie mise à jour pour les versions d’Adobe Commerce

## Qu&#39;est-ce qui change ?

Adobe Commerce fournit des correctifs de qualité pour une version mineure pendant au moins 12 mois à compter de la date de disponibilité générale de la prochaine version mineure du logiciel. La manière dont nous fournissons des correctifs de qualité au cours de cette période change :

* **Politique précédente :** actuellement, les correctifs de qualité de la ligne précédente qui se trouve dans la fenêtre EOS de 12 mois sont fournis via notre version trimestrielle de correctifs, ce qui fait des correctifs trimestriels une combinaison de sécurité et de qualité.
* **Nouvelle stratégie :** à partir de la version 2.4 comme ligne de version mineure la plus récente, les correctifs de version pour la ligne précédente prise en charge (2.3) passeront en sécurité seule. Nous continuerons à fournir des correctifs de qualité pour la ligne précédente prise en charge pendant les 12 mois qui suivent la publication d’une version mineure (comme la version 2.4) et les nouvelles lignes de version mineure suivantes. Toutefois, ces correctifs seront disponibles via l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) et seront axés uniquement sur les problèmes critiques.

## Quand cette politique entre-t-elle en vigueur ?

La publication d’Adobe Commerce 2.3.6 est prévue pour le 15 octobre 2020. Il est prévu qu’il s’agisse de la dernière version de correctif d’Adobe Commerce 2.3 qui inclura à la fois la qualité et la sécurité. Après la version 2.3.6, la ligne 2.3.x deviendra uniquement un problème de sécurité et les problèmes de qualité critiques pour la version 2.3 pourront être résolus via QPT.

>[!NOTE]
>
>La seule fois où nous publierons une version complète de 2.3, c’est si nous devons rester en conformité avec notre pile technologique, comme pour PHP ou Elasticsearch. Cela se passe au 2ème trimestre 2021 avec une mise à jour obligatoire de PHP 7.4, nous allons incrémenter la ligne à 2.3.7. Pour plus d’informations, reportez-vous à l’article DevBlog [Prise en charge de PHP 7.4 pour la ligne de version 2.3.x d’Adobe Commerce](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946).

## Qu’est-ce qu’une version destinée uniquement à la sécurité ?

Les mises à jour de sécurité uniquement contiennent uniquement des correctifs de sécurité et aucune correction de qualité. Notez toutefois que nos versions exclusivement dédiées à la sécurité peuvent inclure des correctifs spécifiques lorsque nous les jugeons absolument essentiels pour exécuter Adobe Commerce.

## Existera-t-il toujours une version destinée uniquement à la sécurité pour la dernière ligne (à compter de la publication, version 2.4) ?

Adobe continuera également à disposer de versions de sécurité uniquement pour la dernière ligne de mise à jour. La procédure à suivre est décrite dans l’article de DevBlog [ Présentation de la nouvelle version de correctif destinée uniquement à la sécurité ](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287) .

## Qu’est-ce que l’outil de correctifs de qualité ?

Consultez l’article [Outil de correctifs de qualité publié : un nouvel outil pour appliquer des correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans notre base de connaissances du support.

## Qui devrait envisager d’utiliser cette nouvelle politique ?

La nouvelle politique vise à créer des parcours permettant aux commerçants de planifier stratégiquement les coûts annuels de développement d’Adobe Commerce, tout en leur permettant de maintenir la sécurité et la qualité critique pendant ces cycles stratégiques. Il peut également être utilisé par les commerçants qui se soucient de la sécurité sur tout le reste et sont généralement heureux de la stabilité de la ligne plus ancienne et soutenue. Les commerçants trouveront peut-être plus facile de planifier et de budgéter ces mises à niveau, car elles seront plus prévisibles.

## Les commerçants devraient-ils toujours effectuer une mise à niveau vers la dernière ligne ?

En fin de compte, tous les commerçants doivent toujours donner la priorité à la planification pour adopter la dernière ligne d&#39;Adobe Commerce en temps opportun. La nouvelle ligne Sécurité uniquement et le nouvel outil QPT ne sont pas destinés à remplacer la feuille de route de mise à niveau stratégique pour les commerçants ; ils offrent plutôt une flexibilité aux commerçants dans la planification de leur feuille de route de mise à niveau et un moyen de réagir rapidement aux problèmes de sécurité/qualité sans avoir à mettre en œuvre une mise à niveau complète.

## Comment puis-je obtenir des correctifs de qualité sur les versions mineures prises en charge qui ne sont pas de la dernière ligne ?

Les correctifs seront disponibles via l’[outil de correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).

## Comment puis-je obtenir des correctifs de qualité sur la dernière ligne ?

La ligne actuelle sera de qualité dans le cadre de la mise à jour trimestrielle. Entre les versions, si vous contactez le support pour un correctif sur la ligne la plus récente, il le fournira via QPT. Ensuite, une fois que vous avez effectué la mise à niveau vers la version qui contient ce correctif, il sera appliqué via le correctif trimestriel.

## Quels types de problèmes de qualité seront corrigés sur les versions mineures prises en charge qui ne sont pas de la dernière ligne ?

Seuls les problèmes de qualité majeurs qui rompent les flux de base seront corrigés dans la ligne précédente (2.3) et diffusés via QPT.

## Des correctifs de qualité seront-ils inclus dans la version trimestrielle des versions mineures prises en charge qui ne sont pas de la dernière ligne ?

Oui, dans le cadre de la ligne consacrée à la sécurité uniquement, nous publions ce qu’Adobe appelle des « correctifs logiciels » sur cette ligne. Il s’agit de problèmes très critiques qui affectent l’application Adobe Commerce.

## Les améliorations de sécurité et le QPT seront-ils fournis en même temps ?

La ligne sécurité seule suivra le calendrier de publication trimestrielle et sera publiée avec la nomenclature -p1. Exemple 2.3.6-p1. La qualité sera publiée ad hoc à mesure que les problèmes de qualité seront découverts et corrigés, et elles seront disponibles via QPT.

## Si j’ai un problème de qualité qui ne sera pas résolu dans les versions mineures prises en charge qui ne sont pas la dernière ligne ou le QPT, que dois-je faire ?

La ligne précédente étant la sécurité uniquement, le principal avantage est de rester sécurisé. Seuls les correctifs pour les problèmes majeurs qui rompent les flux de base seront disponibles via QPT.

Les problèmes qui n’affectent pas les flux principaux ou qui comportent des solutions de contournement seront corrigés uniquement dans la ligne la plus récente. Adobe incite ceux qui souhaitent des correctifs critiques et non critiques à passer à la ligne la plus récente.

## Les mises à niveau seront-elles plus coûteuses ou plus difficiles pour les commerçants s&#39;ils restent sur la ligne de sécurité uniquement jusqu&#39;à ce que la prise en charge de la sécurité soit terminée ?

En théorie, ils devraient être égaux en coût pour le commerçant en termes d&#39;heures de développement tant qu&#39;ils n&#39;ont pas adopté un grand nombre de Patchs Qualité. Si un commerçant estime avoir besoin de plus d’une poignée de correctifs via l’outil QPT, il lui est recommandé d’effectuer en priorité une mise à niveau vers la dernière version d’Adobe Commerce. L’adoption d’un grand nombre de correctifs de qualité, au lieu de la mise à niveau vers la version actuelle d’Adobe Commerce, peut augmenter les coûts de développement et la complexité de la mise à niveau une fois que la ligne dédiée à la sécurité a atteint la fin de la prise en charge.

## Pourquoi dois-je limiter la quantité de correctifs de qualité fournis via QPT ?

En appliquant de nombreux correctifs de qualité individuels, vous rendez votre code Adobe Commerce plus complexe. La complexité supplémentaire peut entraîner des modifications imprévisibles lors de la mise à niveau vers la ligne de mise à jour la plus récente. C&#39;est pourquoi nous recommandons d&#39;utiliser QPT avec parcimonie et uniquement pour les correctifs les plus critiques.

## Qu’en est-il de la conformité des piles technologiques ?

Pendant la durée de vie d’une ligne de version, diverses piles de technologies telles que PHP ou Elasticsearch devront être mises à niveau pour rester conformes. Nous aviserons le plus possible nos commerçants de l&#39;arrivée de ces produits.

Note : Au 2ème trimestre 2021, nous devrons mettre à jour PHP et Redis sur la ligne 2.3.x pour rester en conformité. La ligne sera alors incrémentée à 2.3.7. Pour plus d’informations, reportez-vous à l’article DevBlog [Prise en charge de PHP 7.4 pour la ligne de version 2.3.x d’Adobe Commerce](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946).
