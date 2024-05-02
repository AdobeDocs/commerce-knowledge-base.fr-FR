---
title: Outil de compatibilité de mise à niveau 1.1.0 pour Adobe Commerce
description: L’outil de compatibilité de mise à niveau 1.1.0 est un outil de ligne de commande qui vérifie une instance personnalisée Adobe Commerce par rapport à une version spécifique en analysant tous les modules et le code principal qui y sont installés. Elle renvoie une liste des erreurs, problèmes et avertissements critiques qui doivent être résolus avant la mise à niveau vers la dernière version d’Adobe Commerce.
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Outil de compatibilité de mise à niveau 1.1.0 pour Adobe Commerce

L’outil de compatibilité de mise à niveau 1.1.0 est un outil de ligne de commande qui vérifie une instance personnalisée Adobe Commerce par rapport à une version spécifique en analysant tous les modules et le code principal qui y sont installés. Elle renvoie une liste des erreurs, problèmes et avertissements critiques qui doivent être résolus avant la mise à niveau vers la dernière version d’Adobe Commerce.

## Nouveautés de l’UCT 1.1.0

La version 1.1.0 de l’outil de compatibilité de mise à niveau contient des améliorations importantes, notamment :

* **Validation des modifications des fichiers principaux**: Adobe recommande vivement de ne pas personnaliser le code de produit principal. Avec cette version, nous avons ajouté un point de contrôle permettant aux clients et aux partenaires d’identifier les modifications apportées au code principal afin de comprendre rapidement et rapidement l’impact des modifications. L’ajout de cet outil dans le processus de développement aidera les partenaires et les commerçants à identifier les problèmes de manière proactive, à prévenir les problèmes lors des futures mises à niveau et à réduire le coût total de propriété (TCO).
* **Exportation du rapport dans un fichier JSON**: cette amélioration a été mise en oeuvre suite aux commentaires de la communauté. Désormais, lorsque vous exécutez l’outil, les détails de tous les problèmes identifiés sont exportés vers un fichier JSON afin que les utilisateurs puissent lire, partager et gérer les résultats sans avoir à exécuter à nouveau l’outil.
* **Validations VBE améliorées**: les VBE (Extensions groupées de fournisseurs) ne font pas partie du code principal Adobe Commerce, mais sont testées et prises en charge par Adobe. Avec cette mise à jour, nous validons désormais les VBE en utilisant la même approche que celle que nous utilisons pour le code principal. Cette amélioration aidera les utilisateurs à comprendre clairement les problèmes liés aux personnalisations et au code/à l’environnement de test virtuel principal.
* **Fournir des codes d’erreur**: nous avons introduit des codes d’erreur pour aider les utilisateurs à identifier, comprendre et résoudre les problèmes lors d’une mise à niveau. Les messages d’erreur et d’avertissement fournissent une description claire et une solution suggérée.
* **Possibilité de ne répertorier que les problèmes critiques**: avec cela, les utilisateurs pourront se concentrer uniquement sur les problèmes critiques qui généreront des problèmes lors de la mise à niveau.
* **Problèmes delta entre deux versions**: avec cette amélioration proposée par les membres de notre communauté, les utilisateurs de l’UCT pourront obtenir un delta des problèmes entre deux versions, ce qui leur permettra de se concentrer uniquement sur les nouveaux problèmes introduits pour la version cible qu’ils vont mettre à niveau.

## Quelles versions l’outil peut-il comparer ?

Vous pouvez utiliser l’outil pour comparer n’importe quelle version 2.x.

## Qui peut utiliser l’outil de compatibilité de mise à niveau 1.1.0 ?

Clients Adobe Commerce.

## Installation de l’outil de compatibilité de mise à niveau 1.1.0

Pour les étapes d&#39;installation, voir Adobe Commerce : [Outil de compatibilité de mise à niveau > Installer](https://devdocs.magento.com/upgrade-compatibility-tool/install.html) dans notre documentation destinée aux développeurs. Pour connaître les conditions préalables à l&#39;utilisation de l&#39;outil, reportez-vous à Adobe Commerce : [Outil de compatibilité de mise à niveau](https://devdocs.magento.com/upgrade-compatibility-tool/prerequisites.html) dans notre documentation destinée aux développeurs.

## Quel est le numéro en regard de chaque problème ?

Il s’agit de la référence du message d’erreur qui fournit des informations sur les erreurs qui peuvent se produire lors de l’exécution de l’outil de compatibilité de mise à niveau.

Les messages d’erreur de l’outil de compatibilité de mise à niveau sont classés par niveau (problèmes critiques, erreurs et avertissements) et par type (code principal, code personnalisé et schémas GraphQL). Chaque type contient les informations suivantes :

* Code d’erreur : identifiant attribué par Adobe Commerce au message d’erreur.
* Description de l’erreur : description qui résume la cause de l’erreur.
* Action suggérée pour les erreurs : le cas échéant, fournit des conseils pour dépanner et résoudre l’erreur.
* Les codes sont répertoriés et décrits dans la section [Page de référence des messages d’erreur](https://devdocs.magento.com/upgrade-compatibility-tool/errors.html).

## Où puis-je partager mes commentaires sur l’outil ?

Vous pouvez contacter l’équipe UCT sur notre [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F) slack channel Nous nous réjouissons de recevoir vos commentaires et suggestions pour améliorer l’outil.

## Lecture connexe

* Blog Adobe Commerce : [Présentation de l’outil de compatibilité de mise à niveau (Alpha)](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* ADOBE COMMERCE : [Outil de compatibilité de mise à niveau](https://devdocs.magento.com/upgrade-compatibility-tool/introduction.html) dans notre documentation destinée aux développeurs.
