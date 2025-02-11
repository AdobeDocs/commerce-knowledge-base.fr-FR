---
title: Vérifiez que le correctif ne présente aucun problème avec l’outil de correctifs de qualité d’Adobe Commerce.
description: Cet article présente l’outil de correctifs de la qualité (QPT) et contient des liens vers des ressources expliquant comment l’utiliser.
exl-id: 43393708-3939-449f-a764-b2ac6326165f
feature: Tools and External Services
role: Admin
source-git-commit: ce9c69e12d64b4b4a8e6129783d9b15e95eff867
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Vérifiez que le correctif ne présente aucun problème avec l’outil de correctifs de qualité d’Adobe Commerce.

Cet article présente l’outil de correctifs de la qualité (QPT) et contient des liens vers des ressources expliquant comment l’utiliser.

## Produits et versions concernés

* Adobe Commerce On-premise, toutes les [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce sur les infrastructures cloud, toutes les [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## En quoi consiste l’outil de correctifs de qualité ?

L’[outil de correctifs de qualité](https://github.com/magento/quality-patches) (QPT) est un correctif individuel développé par l’Adobe et la communauté des Magento Open Sources.

Il permet d’effectuer les opérations suivantes :

* appliquez les correctifs de qualité inclus dans le package
* rétablir les correctifs précédemment appliqués
* affichez les informations générales sur les correctifs de qualité disponibles pour la version installée d’Adobe Commerce.

Voici un exemple du tableau d’état auquel vous pouvez accéder pour afficher les correctifs disponibles :

![liste_patches_Magento ](assets/status_table.png)

L’outil a pour but de vous permettre d’utiliser des correctifs en libre-service pour résoudre les problèmes que vous pourriez rencontrer avec Adobe Commerce, ou d’appliquer facilement des correctifs recommandés par la prise en charge d’Adobe Commerce.

>[!NOTE]
>
>QPT est réservé aux correctifs de qualité uniquement. Les correctifs de sécurité sont disponibles dans le Centre de sécurité du Magento [](https://magento.com/security/patches).

## Correctifs disponibles dans l’outil de correctifs de la qualité

Reportez-vous à [Outil de correctifs de qualité](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans notre documentation destinée aux développeurs pour obtenir la liste des correctifs disponibles.

## Installation et utilisation de l’outil de correctifs de qualité

Les commandes d’installation et d’utilisation sont différentes pour Adobe Commerce On-Premise et Adobe Commerce sur l’infrastructure cloud, car pour le cloud, le package QPT est inclus dans le package ece-tools.

### Installation et utilisation de QPT pour Adobe Commerce On-Premise

Consultez le [Guide de mise à jour logicielle > Correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs pour plus d’informations sur l’installation et l’utilisation de QPT pour l’application et le rétablissement des correctifs.

### Installation et utilisation de QPT pour Adobe Commerce sur une infrastructure cloud

Consultez [Cloud for Adobe Commerce > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs pour plus d’informations sur l’installation et l’utilisation de QPT pour appliquer et rétablir des correctifs sur Adobe Commerce sur les infrastructures cloud.

## Lecture connexe

* [Notes de mise à jour de l’outil de correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes) dans notre documentation destinée aux développeurs.
* [Comment appliquer les correctifs de compositeur fournis par Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances d’assistance.

