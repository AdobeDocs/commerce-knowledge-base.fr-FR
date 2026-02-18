---
title: Conseils de test tiers pour Adobe Commerce sur les infrastructures cloud
description: Cet article fournit des options de partage de l’accès avec un tiers à des fins de test/validation lorsque vous rencontrez un problème avec une extension pour Adobe Commerce sur une infrastructure cloud.
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: 9e218e3fadbf9941c94d309fcfb6f258d2f4faf2
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Conseils de test tiers pour Adobe Commerce sur les infrastructures cloud

Cet article fournit des options de partage de l’accès avec un tiers à des fins de test/validation lorsque vous rencontrez un problème avec une extension pour Adobe Commerce sur une infrastructure cloud.
Des procédures et des exigences internes appropriées en matière de sécurité des données doivent être respectées de votre part lorsque vous décidez de la manière de fournir l’accès à un tiers.

## Produits et versions concernés :

* Adobe Commerce sur les infrastructures cloud 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Environnements à utiliser pour les tests

En fonction de vos normes de sécurité internes, vous pouvez choisir de faire appel au service de dépannage tiers sur un environnement local. Si le problème ne peut pas être reproduit localement, vous pouvez fournir un accès à votre environnement cloud. Si vous choisissez de le faire, veillez à respecter vos normes de sécurité internes. Si vous fournissez l’accès à l’un de vos environnements cloud, assurez-vous que votre tiers sait clairement ce qui peut être fait et quelle approbation est requise pour des éléments tels que la réplication uniquement ou l’autorisation de modifications de code. Cela est particulièrement important pour les environnements de production.

## Fournir à des tiers un accès et des données

* Fournissez à votre fournisseur tiers un accès à l’environnement cloud. Articles connexes :

   * [Guide de l&#39;utilisateur du Centre d&#39;aide Adobe Commerce > ACCÈS PARTAGÉ : ACCORDEZ DES PRIVILÈGES À D&#39;AUTRES UTILISATEURS POUR ACCÉDER À VOTRE COMPTE](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guidee#shared-access) dans notre base de connaissances du support.
   * [Partage de votre compte Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-share) dans notre guide de l’utilisateur.

* Créez une image mémoire de la base de données (ou accordez au fournisseur tiers l’accès nécessaire). Vous pouvez le faire à l’aide de l’interface de ligne de commande ou dans Commerce Admin. Cette image mémoire de la base de données obscurcit les données client. Par conséquent, tout ce qu’ils obtiennent est du code, des SKU de produit, etc., aucune donnée propriétaire/client. À titre de référence, utilisez [Partage de votre compte Commerce] (/help/how-to/general/create-database-dump-on-cloud.md) dans notre base de connaissances d’assistance.
* Une fois le test terminé, veillez à révoquer l’accès partagé à votre environnement cloud, comme décrit dans [Guide d’utilisation du centre d’aide Adobe Commerce > Révoquer (supprimer l’accès partagé)](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#revoke-shared-access) dans notre base de connaissances de l’assistance.

## Bonnes pratiques en matière de test

La pratique standard consiste à effectuer un dépannage dans un environnement local. Si le problème ne peut pas être reproduit localement, accédez à Évaluation. Le tiers devra peut-être vérifier en production. Assurez-vous que votre tiers sait qu’il ne doit essayer que de reproduire le problème dans les environnements de production et d’évaluation et qu’il ne doit pas apporter de modifications au code. S’il doit apporter des modifications au code, il doit d’abord obtenir votre autorisation.

## Lecture connexe

* [Bonnes pratiques relatives à l’utilisation d’extensions tierces dans Adobe Commerce](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) dans notre base de connaissances d’assistance.
