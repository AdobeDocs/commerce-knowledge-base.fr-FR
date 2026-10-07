---
title: Puis-je installer des applications tierces sur mon instance cloud ?
description: Non. L’installation d’applications tierces (telles que WordPress ou Drupal) sur Adobe Commerce sur des serveurs d’infrastructure cloud n’est pas autorisée. Vous devez héberger ces applications sur des serveurs externes.
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%
---
# Puis-je installer des applications tierces sur mon instance cloud ?

Non. L’installation d’applications tierces (telles que WordPress ou Drupal) sur Adobe Commerce sur des serveurs d’infrastructure cloud n’est pas autorisée. Vous devez héberger ces applications sur des serveurs externes.

## Motifs

### Conditions de l’accord de service

L’édition d’Adobe Commerce sur les infrastructures cloud [contrat de service](https://magento.com/legal/terms/cloud-terms) énonce ce qui suit à son article 18 :

> Le Client accepte qu&#39;Adobe Commerce et le Service ne soient pas utilisés pour héberger d&#39;autres applications logicielles tierces qui ne sont pas directement dépendantes du Logiciel.

En tant que solution cloud, Adobe assume l’entière responsabilité de la sécurité de votre serveur. Pour garantir un niveau de sécurité élevé, nous autorisons uniquement l’hébergement de l’application Adobe Commerce sur le serveur cloud dédié.

### Conformité PCI

En tant que fournisseur de solution de niveau 1 certifié PCI, Adobe Commerce sur l’infrastructure cloud doit respecter la norme PCI Data Security et s’assurer de :

>... Développer et maintenir des systèmes et des applications sécurisés
> ([Approche Adobe de la conformité PCI](https://magento.com/pci-compliance) Exigence 6, maintenir un programme de gestion des vulnérabilités)

Étant donné qu’Adobe ne peut pas garantir la conformité PCI des applications tierces, l’installation de telles applications sur des serveurs cloud n’est pas autorisée.

## Conseil : utilisation des extensions Commerce Marketplace pour de meilleures intégrations

Afin d&#39;améliorer l&#39;intégration de votre application Adobe Commerce sur les infrastructures cloud avec les solutions tierces hébergées sur des serveurs externes, nous vous conseillons d&#39;utiliser les extensions [Commerce Marketplace](https://marketplace.magento.com) susceptibles de répondre à vos besoins.
