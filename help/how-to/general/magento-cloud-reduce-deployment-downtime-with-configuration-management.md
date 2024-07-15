---
title: Réduction du temps d’arrêt du déploiement sur Adobe Commerce sur l’infrastructure cloud
description: Pour réduire considérablement les temps d’arrêt de la maintenance et assurer une configuration efficace de votre magasin dans tous les environnements, Adobe Commerce sur l’infrastructure cloud fournit la fonctionnalité **Configuration Management**. Pour Adobe Commerce sur les mises en oeuvre de l’infrastructure cloud 2.2.x et versions ultérieures, cette fonctionnalité prend en charge les concepts et options de déploiement de pipeline avec des étapes réduites.
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: 23d957ceac17f9989d14b215582304199d398545
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Réduction du temps d’arrêt du déploiement sur Adobe Commerce sur l’infrastructure cloud

Pour réduire considérablement les temps d’arrêt de la maintenance et assurer une configuration efficace de votre magasin dans tous les environnements, Adobe Commerce sur l’infrastructure cloud fournit la fonctionnalité **Configuration Management**. Pour Adobe Commerce sur les mises en oeuvre de l’infrastructure cloud 2.2.x et versions ultérieures, cette fonctionnalité prend en charge les concepts et options de déploiement de pipeline avec des étapes réduites.

## Vue d’ensemble

Les problèmes douloureux et chronophages liés au déploiement de votre magasin web incluent les suivants :

* **Application de la même configuration à tous les environnements.** Normalement, vous devez saisir des configurations manuellement ou par le biais de mises à jour de base de données complexes. Avec Configuration Management, vous exportez les configurations de la base de données dans un fichier unique afin de les transmettre ultérieurement avec votre code de votre environnement de développement local vers Intégration, Évaluation et Production.

* **Temps d’arrêt du site lors du déploiement de contenu statique.** En règle générale, le contenu statique est déployé pendant la [phase de déploiement](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase). Cela peut prendre jusqu’à 30 minutes ou plus, ce qui n’est pas acceptable pour les entreprises. Configuration Management déplace le déploiement de contenu statique vers la [phase de création](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase), qui ne nécessite pas de temps d’arrêt.

## Versions de technologie

* Adobe Commerce sur l’infrastructure cloud **2.1.4** et versions ultérieures pour la gestion de la configuration
* Adobe Commerce sur l’infrastructure cloud **2.2** et versions ultérieures pour la gestion de configuration/le déploiement du pipeline

## Présentation de la gestion des configurations

Pour faire court, le processus Configuration Management (également appelé déploiement du pipeline) extrait tous les paramètres de configuration de votre Adobe Commerce sur la mise en oeuvre de l’infrastructure cloud (base de données) dans un seul fichier PHP. Ensuite, vous ajoutez le fichier à votre validation Git et vous le transmettez dans tous vos environnements.

Les avantages sont les suivants :

* **Paramètres cohérents dans tous les environnements :** tous les paramètres exportés vers le fichier de configuration sont verrouillés (les champs correspondants dans l’administrateur de Commerce sont en lecture seule), ce qui garantit des configurations cohérentes lorsque vous placez le fichier dans tous vos environnements.
* **Temps d’arrêt réduit :** le déploiement de fichiers statiques passe de la [phase de déploiement](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase) (qui nécessite que le site soit en mode de maintenance) à la [phase de création](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase) (lorsque le site n’est pas en mode de maintenance et ne sera pas supprimé en cas d’erreurs ou de problèmes).
* **Données sensibles protégées :** avec Adobe Commerce sur l’infrastructure cloud 2.2 et versions ultérieures, le processus exporte également toutes les données sensibles (par exemple, les informations d’identification de la passerelle de paiement) vers le fichier `env.php`. Ce fichier ne doit être enregistré que dans l’environnement dans lequel il est créé et ne doit pas être envoyé avec vos branches Git.

Nous vous recommandons vivement d’appliquer l’approche de gestion de configuration à votre déploiement.

## Gestion des configurations dans notre documentation destinée aux développeurs

* [Gestion des configurations pour **2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) et l’ [exemple](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) dans le *Guide de l’infrastructure cloud d’Adobe Commerce*
* [Gestion des configurations pour **2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) et l’ [exemple](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) dans le *Guide de l’infrastructure cloud d’Adobe Commerce*
* [Mise à niveau de la section 2.0.X ou 2.1.X](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html#upgrade-from-older-versions) de la rubrique *Mise à niveau d’Adobe Commerce sur l’infrastructure cloud*
* [Déploiement de pipeline](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html) dans le *Guide de configuration d’Adobe Commerce on cloud infrastructure* - Pour Adobe Commerce sur l’infrastructure cloud, vous n’avez pas besoin de suivre les instructions de ce guide. Le contenu est strictement à titre de référence. Nous fournissons déjà le serveur de génération, les environnements d’intégration et plus encore avec Adobe Commerce sur l’infrastructure cloud.
