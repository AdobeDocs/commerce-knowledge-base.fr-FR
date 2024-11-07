---
title: Outil de compatibilité de mise à niveau 1.1.0 pour Adobe Commerce
description: L’outil de compatibilité de mise à niveau 1.1.0 est un outil de ligne de commande qui vérifie une instance personnalisée Adobe Commerce par rapport à une version spécifique en analysant tous les modules et le code principal qui y sont installés. Elle renvoie une liste des erreurs, problèmes et avertissements critiques qui doivent être résolus avant la mise à niveau vers la dernière version d’Adobe Commerce.
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Outil de compatibilité de mise à niveau 1.1.0 pour Adobe Commerce

L’outil de compatibilité de mise à niveau 1.1.0 est un outil de ligne de commande qui vérifie une instance personnalisée Adobe Commerce par rapport à une version spécifique en analysant tous les modules et le code principal qui y sont installés. Elle renvoie une liste des erreurs, problèmes et avertissements critiques qui doivent être résolus avant la mise à niveau vers la dernière version d’Adobe Commerce.

## Nouveautés de l’UCT 1.1.0

La version 1.1.0 de l’outil de compatibilité de mise à niveau contient des améliorations importantes, notamment :

* **Valider les modifications de fichier principal** : Adobe recommande vivement de ne pas personnaliser le code de produit principal. Avec cette version, nous avons ajouté un point de contrôle permettant aux clients et aux partenaires d’identifier les modifications apportées au code principal afin de comprendre rapidement et rapidement l’impact des modifications. L’ajout de cet outil dans le processus de développement aidera les partenaires et les commerçants à identifier les problèmes de manière proactive, à prévenir les problèmes lors des futures mises à niveau et à réduire le coût total de propriété (TCO).
* **Exportez le rapport dans un fichier JSON** : cette amélioration a été mise en oeuvre suite aux commentaires de la communauté. Désormais, lorsque vous exécutez l’outil, les détails de tous les problèmes identifiés sont exportés vers un fichier JSON afin que les utilisateurs puissent lire, partager et gérer les résultats sans avoir à exécuter à nouveau l’outil.
* **Validations VBE améliorées** : les VBE (Extensions groupées de fournisseurs) ne font pas partie du code de base Adobe Commerce, mais sont testées et prises en charge par Adobe. Avec cette mise à jour, nous validons désormais les VBE en utilisant la même approche que celle que nous utilisons pour le code principal. Cette amélioration aidera les utilisateurs à comprendre clairement les problèmes liés aux personnalisations et au code/à l’environnement de test virtuel principal.
* **Fournir des codes d’erreur** : nous avons introduit des codes d’erreur pour aider les utilisateurs à identifier, comprendre et résoudre les problèmes lors d’une mise à niveau. Les messages d’erreur et d’avertissement fournissent une description claire et une solution suggérée.
* **Possibilité de ne répertorier que les problèmes critiques** : grâce à cela, les utilisateurs pourront se concentrer uniquement sur les problèmes critiques qui généreront des problèmes lors de la mise à niveau.
* **Problèmes delta entre deux versions** : avec cette amélioration proposée par les membres de notre communauté, les utilisateurs de l&#39;UCT pourront obtenir un delta des problèmes entre deux versions, ce qui leur permettra de se concentrer uniquement sur les nouveaux problèmes introduits pour la version cible qu&#39;ils vont mettre à niveau.

## Quelles versions l’outil peut-il comparer ?

Vous pouvez utiliser l’outil pour comparer n’importe quelle version 2.x.

## Qui peut utiliser l’outil de compatibilité de mise à niveau 1.1.0 ?

Clients Adobe Commerce.

## Installation de l’outil de compatibilité de mise à niveau 1.1.0

Pour connaître les étapes d&#39;installation, reportez-vous à Adobe Commerce : [Outil de compatibilité de mise à niveau > Installer](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run) dans notre documentation destinée aux développeurs. Pour connaître les conditions préalables à l’utilisation de l’outil, reportez-vous à Adobe Commerce : [Upgrade Compatibility Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/prerequisites) dans la documentation destinée aux développeurs.

## Quel est le numéro en regard de chaque problème ?

Il s’agit de la référence du message d’erreur qui fournit des informations sur les erreurs qui peuvent se produire lors de l’exécution de l’outil de compatibilité de mise à niveau.

Les messages d’erreur de l’outil de compatibilité de mise à niveau sont classés par niveau (problèmes critiques, erreurs et avertissements) et par type (code principal, code personnalisé et schémas GraphQL). Chaque type contient les informations suivantes :

* Code d’erreur : identifiant attribué par Adobe Commerce au message d’erreur.
* Description de l’erreur : description qui résume la cause de l’erreur.
* Action suggérée pour les erreurs : le cas échéant, fournit des conseils pour dépanner et résoudre l’erreur.
* Les codes sont répertoriés et décrits sur la [page de référence du message d’erreur](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/reporting/error-messages).

## Où puis-je partager mes commentaires sur l’outil ?

Vous pouvez contacter l&#39;équipe UCT sur notre canal de slack [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Nous nous réjouissons de recevoir vos commentaires et suggestions pour améliorer l’outil.

## Lecture connexe

* Blog Adobe Commerce : [Présentation de l’outil de compatibilité de mise à niveau (Alpha)](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* Adobe Commerce : [Mise à niveau de l’outil de compatibilité](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview) dans la documentation destinée aux développeurs.
