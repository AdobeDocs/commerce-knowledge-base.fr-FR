---
title: Conseils sur les tests tiers pour Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit des options pour le partage de l’accès avec un tiers à des fins de test/validation lorsque vous rencontrez un problème avec une extension pour Adobe Commerce sur l’infrastructure cloud.
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Conseils sur les tests tiers pour Adobe Commerce sur l’infrastructure cloud

Cet article fournit des options pour le partage de l’accès avec un tiers à des fins de test/validation lorsque vous rencontrez un problème avec une extension pour Adobe Commerce sur l’infrastructure cloud.
Les procédures et exigences de sécurité des données internes appropriées doivent être suivies de votre part lorsque vous décidez de la manière de fournir l’accès à un tiers.

## Produits et versions concernés :

* Adobe Commerce sur l’infrastructure cloud 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Environnements à utiliser pour les tests

En fonction de vos normes de sécurité interne, vous pouvez choisir de résoudre les problèmes tiers dans un environnement local. Si le problème ne peut pas être reproduit localement, vous pouvez souhaiter fournir un accès à votre environnement cloud. Si vous choisissez de le faire, veillez à respecter vos normes de sécurité interne. Si vous fournissez l’accès à l’un de vos environnements cloud, assurez-vous que votre tiers sait clairement ce qui peut être fait et quelle approbation est requise pour des éléments tels que la réplication uniquement ou la permission de modifier le code. Ceci est particulièrement important pour les environnements de production.

## Fournir à des tiers un accès et des données

* Fournissez à votre fournisseur tiers un accès à l’environnement cloud. Articles connexes :

   * [Guide de l’utilisateur du centre d’aide Adobe Commerce > ACCÈS PARTAGÉ : OCTROYER DES DROITS À D’AUTRES UTILISATEURS POUR ACCÉDER À VOTRE COMPTE](/help/help-center-guide/help-center/magento-help-center-user-guide.md#shared-access) dans notre base de connaissances de soutien.
   * [Partage de votre compte Commerce](https://docs.magento.com/user-guide/magento/magento-account-share.html) dans notre guide d’utilisation.

* Créez un vidage de base de données (ou autorisez le fournisseur tiers à le faire). Vous pouvez le faire à l’aide de l’interface de ligne de commande ou dans l’administrateur Commerce. Ce fichier de vidage DB obscurcit les données des clients, de sorte que tout ce qu’ils obtiennent est le code et les SKU du produit, etc., pas de données propriétaires/clients. À titre de référence, utilisez [Partage de votre compte Commerce] (/help/how-to/general/create-database-dump-on-cloud.md) dans notre base de connaissances du support.
* Une fois le test terminé, veillez à révoquer l’accès partagé à votre environnement cloud, comme décrit dans la section [Guide de l’utilisateur du centre d’aide Adobe Commerce > Révoquer (supprimer l’accès partagé)](/help/help-center-guide/help-center/magento-help-center-user-guide.md#revoke-shared-access) dans notre base de connaissances de soutien.

## Tester les bonnes pratiques

La pratique standard consiste à résoudre les problèmes dans un environnement local. Si le problème ne peut pas être reproduit localement, accédez à Évaluation. Il se peut que le tiers doive vérifier la production. Assurez-vous que votre tiers sait qu’il s’agit uniquement d’essayer de reproduire le problème dans les environnements de production et d’évaluation et de ne pas apporter de modifications au code. S’il doit apporter des modifications au code, il doit d’abord obtenir votre autorisation.

## Lecture connexe

* [Bonnes pratiques relatives à l’utilisation d’extensions tierces dans Adobe Commerce](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) dans notre base de connaissances de soutien.
