---
title: Correctif du problème Adobe Commerce avec l’outil Correctifs de qualité
description: Cet article présente un aperçu de l’outil de correctifs de qualité (QPT) et des liens vers des ressources expliquant comment l’utiliser.
exl-id: 43393708-3939-449f-a764-b2ac6326165f
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Correctif du problème Adobe Commerce avec l’outil Correctifs de qualité

Cet article présente un aperçu de l’outil de correctifs de qualité (QPT) et des liens vers des ressources expliquant comment l’utiliser.

## Produits et versions concernés

* Adobe Commerce sur site, toutes les [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce sur l’infrastructure cloud, toutes les [ versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Que sont les outils de correctifs de qualité ?

L’ [outil de correctifs de qualité](https://github.com/magento/quality-patches) (QPT) sont des correctifs individuels développés par Adobe et la communauté des Magento Open Sources.

Il vous permet d’effectuer les opérations suivantes :

* appliquer des correctifs de qualité inclus dans le package ;
* rétablir les correctifs précédemment appliqués
* consultez les informations générales sur les correctifs de qualité disponibles pour la version installée d’Adobe Commerce.

Voici un exemple du tableau d’état pour afficher les correctifs disponibles :

![}Magento_Correctifs_list](assets/status_table.png)

L’outil a pour but de vous permettre d’utiliser en libre-service des correctifs pour les problèmes que vous pouvez rencontrer avec Adobe Commerce ou d’appliquer facilement des correctifs suggérés par le support d’Adobe Commerce.

>[!NOTE]
>
>QPT est réservé aux correctifs de qualité. Les correctifs de sécurité sont disponibles dans le [Centre de sécurité Magento](https://magento.com/security/patches).

## Correctifs disponibles dans l’outil Correctifs de qualité

Pour obtenir la liste des correctifs disponibles, reportez-vous à la section [Outil de correctifs de qualité](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans la documentation destinée aux développeurs.

## Comment installer et utiliser l’outil Correctifs de qualité

Les commandes d’installation et d’utilisation sont différentes pour Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud, car pour le cloud, le package QPT est inclus dans le package ece-tools.

### Comment installer et utiliser QPT pour Adobe Commerce sur site

Pour plus d’informations sur l’installation et l’utilisation de QPT pour appliquer et rétablir des correctifs, reportez-vous au [Guide de mise à jour de logiciel > Patching](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans la documentation destinée aux développeurs.

### Comment installer et utiliser QPT pour Adobe Commerce sur l’infrastructure cloud

Pour plus d’informations sur l’installation et l’utilisation du protocole QPT pour l’application et la restauration de correctifs sur Adobe Commerce sur l’infrastructure cloud, reportez-vous à la section [Cloud for Adobe Commerce > Apply patches](https://devdocs.magento.com/cloud/project/project-patch.html) dans la documentation destinée aux développeurs.

## Lecture connexe

* [Notes de mise à jour de l’outil de correctifs de qualité](https://devdocs.magento.com/quality-patches/release-notes.html) dans la documentation destinée aux développeurs.
* [Comment appliquer les correctifs de compositeur fournis par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.
