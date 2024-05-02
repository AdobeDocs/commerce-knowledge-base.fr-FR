---
title: Puis-je installer des applications tierces sur mon instance cloud ?
description: Non. L’installation d’applications tierces (telles que WordPress ou Drupal) sur Adobe Commerce sur des serveurs d’infrastructure cloud n’est pas autorisée. Vous devez héberger ces applications sur des serveurs externes.
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Puis-je installer des applications tierces sur mon instance cloud ?

Non. L’installation d’applications tierces (telles que WordPress ou Drupal) sur Adobe Commerce sur des serveurs d’infrastructure cloud n’est pas autorisée. Vous devez héberger ces applications sur des serveurs externes.

## Raisons

### Conditions d&#39;utilisation du contrat

Adobe Commerce on Cloud Infrastructure Edition [Contrat de conditions de service](https://magento.com/legal/terms/cloud-terms) L&#39;article 18 stipule ce qui suit :

> Le client accepte qu’Adobe Commerce et le service ne soient pas utilisés pour héberger d’autres applications logicielles tierces qui ne dépendent pas directement du logiciel.

En tant que solution cloud, Adobe assume l’entière responsabilité de la sécurité de votre serveur. Pour garantir une sécurité élevée, nous autorisons uniquement l’hébergement de l’application Adobe Commerce sur le serveur cloud dédié.

### Conformité PCI

En tant que fournisseur de solutions de niveau 1 certifié PCI, Adobe Commerce sur l’infrastructure cloud doit respecter la norme de sécurité des données PCI et s’assurer que :

>.. Développement et maintenance de systèmes et d’applications sécurisés
> ([Approche Adobe de la conformité PCI](https://magento.com/pci-compliance) Condition 6, maintien d’un programme de gestion des vulnérabilités)

Comme Adobe ne peut pas garantir la conformité PCI des applications tierces, l’installation de ces applications sur les serveurs cloud n’est pas autorisée.

## Conseil : Utilisation d’extensions Commerce Marketplace pour de meilleures intégrations

Pour améliorer l’intégration de votre application Adobe Commerce sur l’infrastructure cloud avec les solutions tierces hébergées sur des serveurs externes, nous vous encourageons à utiliser la variable [Commerce Marketplace](https://marketplace.magento.com) des extensions qui peuvent convenir à votre objectif.
